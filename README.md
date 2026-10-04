#!/usr/bin/env python3
"""
8DoTs Interactive Session Energy Profiler (Prototype)
Measures the energy of individual user actions on a local app with minimal overhead.
"""

import sys
import os
import time
from typing import List, Dict, Any

# Ensure we can import from the parent dol8 directory
sys.path.append(os.path.abspath(os.path.join(os.path.dirname(__file__), '..')))

try:
    from dol8.rapl import RAPLReader, RaplUnavailable
except ImportError:
    print("Error: Could not import dol8.rapl. Make sure you are in the correct directory.")
    sys.exit(1)


class OptimizedSessionProfiler:
    """A low-overhead profiler for interactive sessions."""
    
    def __init__(self):
        self.reader = RAPLReader()
        self._file_handles = {}
        self._ranges = {}
        self.actions: List[Dict[str, Any]] = []
        self.session_start_time = 0.0
        self.total_energy_joules = 0.0

    def start(self):
        """Initialize RAPL and cache file handles for zero-overhead reading."""
        if not self.reader.available():
            raise RaplUnavailable(self.reader.unavailable_reason)
        
        # 🚀 OPTIMIZATION: Cache file handles to avoid open/close syscall overhead
        domains = self.reader.domains()
        self._ranges = self.reader.ranges()
        for domain, path_str in domains.items():
            self._file_handles[domain] = open(path_str, "r", encoding="ascii")
            
        self.session_start_time = time.perf_counter()
        print("✅ Profiler started. RAPL domains initialized with cached file handles (Zero Overhead).")

    def _read_energy_now(self) -> Dict[str, int]:
        """Read current energy with minimal overhead using cached handles."""
        readings = {}
        for domain, handle in self._file_handles.items():
            handle.seek(0)  # Rewind to the beginning of the file
            readings[domain] = int(handle.read().strip())
        return readings

    def stop(self):
        """Clean up file handles to prevent resource leaks."""
        for handle in self._file_handles.values():
            try:
                handle.close()
            except Exception:
                pass
        self._file_handles = {}

    def record_action(self, action_name: str, last_readings: Dict[str, int]) -> Dict[str, int]:
        """Record a single action's energy and time."""
        current_time = time.perf_counter()
        current_readings = self._read_energy_now()
        
        # Calculate delta using 8DoTs' built-in wrap-correction logic
        delta = self.reader.delta(last_readings, current_readings, self._ranges)
        energy_joules = sum(delta.values())
        
        # Calculate duration since the last action (or session start)
        last_action_time = self.actions[-1]["end_time"] if self.actions else self.session_start_time
        duration_s = current_time - last_action_time
        avg_watts = energy_joules / duration_s if duration_s > 0 else 0.0
        
        action_data = {
            "id": len(self.actions) + 1,
            "name": action_name,
            "duration_s": round(duration_s, 3),
            "energy_j": round(energy_joules, 3),
            "avg_watts": round(avg_watts, 3),
            "end_time": current_time
        }
        
        self.actions.append(action_data)
        self.total_energy_joules += energy_joules
        
        return current_readings

    def print_report(self, target_url: str):
        """Print a professional, aligned terminal report."""
        if not self.actions:
            print("\n⚠️ No actions recorded.")
            return

        total_time = round(time.perf_counter() - self.session_start_time, 2)
        
        # Find insights
        max_energy_action = max(self.actions, key=lambda x: x["energy_j"])
        max_time_action = max(self.actions, key=lambda x: x["duration_s"])

        print("\n" + "=" * 85)
        print(" 🚀 8DoTs INTERACTIVE SESSION REPORT (High-Resolution Estimate) 🚀 ")
        print("=" * 85)
        print(f" Target URL/App : {target_url}")
        print(f" Total Time     :{total_time} seconds")
        print(f" Total Energy   : {self.total_energy_joules:.3f} Joules")
        print(f" Actions Logged : {len(self.actions)}")
        print("-" * 85)
        print(f" {'#':<3} | {'Action Description':<25} | {'Time (s)':<8} | {'Energy (J)':<10} | {'Avg Watts':<9}")
        print("-" * 85)
        
        for a in self.actions:
            print(f" {a['id']:<3} | {a['name']:<25} | {a['duration_s']:<8} | {a['energy_j']:<10} | {a['avg_watts']:<9}")
            
        print("-" * 85)
        print(" 💡 INSIGHTS:")
        print(f"   - Most energy-intensive: '{max_energy_action['name']}' ({max_energy_action['energy_j']} J)")
        print(f"   - Longest duration     : '{max_time_action['name']}' ({max_time_action['duration_s']} s)")
        print("=" * 85 + "\n")


def main():
    print("🔋 8DoTs Interactive Session Profiler (Prototype)")
    print("Measure the energy of individual clicks/actions with minimal overhead.\n")
    
    target_url = input("Enter target URL or App Name (e.g., http://localhost:3000): ").strip()
    if not target_url:
        target_url = "Unknown Localhost"

    profiler = OptimizedSessionProfiler()
    
    try:
        profiler.start()
    except RaplUnavailable as e:
        print(f"\n❌ Error: {e}")
        print("💡 Tip: Ensure you are on bare-metal Linux with RAPL support.")
        sys.exit(1)

    print("\n" + "-" * 70)
    print(" INSTRUCTIONS:")
    print(" 1. Open your app/website in the browser.")
    print(" 2. Perform an action (e.g., click a button, submit a form).")
    print(" 3. Switch back to this terminal and press ENTER.")
    print(" 4. (Optional) Type a short name for the action (e.g., 'Clicked Login'), or just press ENTER for a default name.")
    print(" 5. Type 'q' or 'quit' and press ENTER to finish and see the report.")
    print("-" * 70 + "\n")

    last_readings = profiler._read_energy_now()
    
    while True:
        try:
            user_input = input(f"👉 Press ENTER after Action {len(profiler.actions) + 1} (or 'q' to quit): ").strip().lower()
            
            if user_input in ['q', 'quit', 'exit']:
                break
            
            # Use user input as action name, or default to "Action X"
            action_name = user_input if user_input else f"Action {len(profiler.actions) + 1}"
             
            print("  ⏳ Measuring...", end="\r")
            last_readings = profiler.record_action(action_name, last_readings)
            # The spaces at the end clear the line so "Measuring..." doesn't overlap
            print(f"  ✅ Recorded: '{action_name}'                     ") 
            
        except KeyboardInterrupt:
            print("\n\n⚠️ Session interrupted by user.")
            break

    profiler.stop()
    profiler.print_report(target_url)


if name == "__main__":
    main()

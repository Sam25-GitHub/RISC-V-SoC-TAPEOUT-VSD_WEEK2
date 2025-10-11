
# 1️⃣ Read Liberty libraries (standard cells + analog macro models)
# These provide the timing, power, and functional data for STA analysis
read_liberty /data/Desktop/RISC_V_SoC_PROG_2025/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_liberty /data/Desktop/RISC_V_SoC_PROG_2025/VSDBabySoC/src/lib/avsdpll.lib
read_liberty /data/Desktop/RISC_V_SoC_PROG_2025/VSDBabySoC/src/lib/avsddac.lib

# 2️⃣ Read synthesized Verilog netlist
# The post-synthesis netlist contains mapped gates and connects to Liberty timing info
read_verilog /data/Desktop/RISC_V_SoC_PROG_2025/VSDBabySoC/src/netlist/vsdbabysoc.synth.v

# 3️⃣ Link the top-level design
# This prepares the design hierarchy for STA analysis
link_design vsdbabysoc

# 4️⃣ Read the timing constraints (clocks, I/O delays, etc.)
# Constraints from synthesis, defining clock periods, input/output delays
read_sdc /data/Desktop/RISC_V_SoC_PROG_2025/VSDBabySoC/src/constraints/vsdbabysoc_synthesis.sdc

# 5️⃣ Report timing checks (setup/hold) with detailed fields
# Generates min/max path delays, including slew, capacitance, input pins, nets, fanout
report_checks -path_delay min_max -fields {slew capacitance input_pins nets fanout} -digits 3 > /data/Desktop/RISC_V_SoC_PROG_2025/VSDBabySoC/reports/post_synth_timing.rpt

# 6️⃣ Optionally, report timing summary metrics
# Useful to quickly identify worst-case slack, skew, and setup violations
report_tns         ;# Total Negative Slack
report_wns         ;# Worst Negative Slack
report_clock_skew  ;# Clock Skew Analysis


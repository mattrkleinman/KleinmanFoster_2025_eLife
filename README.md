# KleinmanFoster_2025_eLife
Data set for Kleinman and Foster, 2025, "Spatial localization of hippocampal replay requires dopamine signaling"

The top level directories correspond to data from Experiment 1.

Each main directory indicates the experimental group (Exp for experimental and Con for control) and subject ID (1-4 for Exp, 1-3 for Con). Within each subject directory are session directories, labeled by the date and session of the day. For example, "Con_1\20210601_run2" is the 2nd session recorded on 2021/06/01 for control subject 1).

Each session directory includes up to 4 files. Sessions that only recorded local field potentials for sharp-wave ripple analyses include "session_info.mat" and "ripple_events.mat". Sessions that also recorded spiking of individual neurons additionally include "spike_data.mat" and "sdes.mat". The descriptions of each file are below:

session_info: a structure containing session information and behavioral data. Fields include: 
  1) position: the linearized, smoothed position in cm
  2) velocity: the first column is time in seconds since recording began and the second column is instantaneous velocity in cm/s
  3) reward_ends: the position bin used as a threshold for detecting when the subject approached the "left" reward end (low position values) and "right" reward end (high position values)
  4) incr_end: the location at which reward was increased in Epoch 2, with "1" indicating the "left"/low position value end of the track and "2" indicating the "right"/high position value end.
  5) epoch_change: each row indicates the transition between epochs, indexed to the time of that entry in the velocity field, with the first value indicating the end of epoch n and the 2nd value the beginning of epoch n+1; e.g., [12650,12651; 25160,25161] indicates a transition from Epoch 1 to Epoch 2 at time velocity(12650,1), and a transition from Epoch 2 to Epoch 3 at time velocity(25160,1)
  6) left_visit: each row is a single visit to the "left" reward end, with the first value being the entrance, when position first was below reward_ends(1), and the second value being the exit, when position was last below reward_ends(2)
  7) right_visit: same as left_visit, but for the other reward end

ripple_events: an n by 4 array, with each row corresponding to the nth ripple that passed detection criteria, and the columns corresponding to (1) the time of ripple onset, (2) the time of ripple offset, (3) the time of peak ripple power, and (4) the position at ripple onset

sdes: an n by 4 array, identical to ripple_events but for spike density events that passed detection criteria

spike_data: an n by 3 array, with each row corresponding to the nth detected spike, and the columns corresponding to (1) the time of the spike, (2) the cluster ID of the spike, and (3) the tetrode ID of the spike

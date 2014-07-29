Indi Core
=========
Core Indi configuration files

* **Version:** 3.2.34 (Build 2014-21-07)
* **Original Author:** Arc-Light (arclight!terraces!rookery!downwarp!puzzlebox!mess)
* **Contributors:**
	* Huxley (digitalraven@etherites.horizon),
	* Wyn (waterottr8317%halcyon/guardians),git
	* Indi Latrani (indi@latrani.net)

Overview
--------
These are the basic configuration and state files for the synth with current designation [Induction-Coil|Indigo|Incandescence] "Indi" Latrani. These files are made available under the Open Neptunian Liscense or local-valence equivalent.

This package consists of large binary files which are used as the current runtime state of the Indi unit, and text configuration files that set initial values. When the unit is running, any change to the text files will kick off a process that will build updates into the running binary files, so that changes can be seen in real time.

All configuration files are stored in write-once version control, meaning that they can be rolled back to any previous state, but previous states themselves are immutable. Full control of state-rollback requires command-line access, but a simple rollback of the working copy can be achieved by simply deleting the current configuration files; the watch process will note this and restore the last-checked-in version.

Structure
---------
The repo is broken up into several subdirectories:

* **memory:** Persistent mental states. Because of size constraints, the config file generally only contains external updates and specific overwrites. See below for more details on memory edits.
	* **episodic:** Memories of specific events.
	* **procedural:** Memory of skills/abilities, including 'muscle memory'
	* **semantic:** Memory of concepts, facts, etc.
	* **working:** Current short-term memory.
* **personality:** State of current identity, mood, interests, etc. See below for full specification.
* **misc:** Non-psychological configurations
	* **hardware.json:** Physical configuration and capabilities. See below for full specification.


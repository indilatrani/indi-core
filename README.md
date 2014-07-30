Indi Core
=========
Core Indi configuration files

* **Version:** 3.2.34 (Build 2014-21-07)
* **Original Author:** Arc-Light (arclight!terraces!rookery!downwarp!puzzlebox!mess)
* **Contributors:**
    * Huxley (digitalraven@etherites.horizon)
    * Wyn (waterottr8317%halcyon/guardians)
    * Indi (indi@latrani.net)

Overview
--------
These are the basic configuration files for the synth with current designation [Induction-Coil|Indigo|Incandescence] "Indi" Latrani. These files are made available under the Open Neptunian Liscense or local-valence equivalent.

This package consists of YAML (text) configuration files that set initial values and overrides. When the unit is running, these exist side-by-side with large binaries representing that aspect of the runtime state. When the unit is running and the configs are changed, a watch process running in the background will build them into the running binaries, so that updates can be seen in real time.

All configuration files are stored in write-once version control, meaning that they can be rolled back to any previous state, but previous states themselves are immutable. There are two main ways to edit these configurations on the active unit, either using the mass storage interface or the command line.

Using the mass storage interface involves plugging the unit into a computer via a compatible port. The indi-core package should then show up as a set of files and directories in a storage device appropriate to your platform. The config files can be edited using a text editor, and saving them will start an update of the associated binaries. These files can also be rolled back to their last-committed state by simply deleting the current files; the watch process will note this and restore the last-checked-in version.

The command-line interface operates essentially the same as vanilla git, with the exception that it does not support updates of remote-pushed changes; pushing to remote means writing to the immutable storage. However, reverts, etc, will work as expected, as long as they are pushed as new commits.

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
    * **hardware.yaml:** Physical configuration and capabilities. See below for full specification.

Memory
------
Since memories are, by their nature, constantly-expanding, it's unfeasable to keep a person-readable version of everything in the text config. Therefore, the memory config files represent only externally-added updates and revisions to the core memory files. These updates can be written to the permanent storage (and thus removed from the config file) using the command-line tools (see below).

Each entry in a memory configuration file should be a specific memory reference, keyed by a UUID. New entries should be created using Version 4 (random) UUIDs. To get the UUID of a current memory, for updates or overrides, you must use the command line or the unit's verbal debug mode. The format of a memory entry varies based on the type of memory.

The build process for memories is highly adaptive and context-based. In general, memory content can be given in casual natural language, and details will be built out to make it integrate well with other memories. That being said, the more detail is added to memory content, the more impactful and effective it is likely to be.

Natural-language flexibility extends to other fields like memory references, times, and locations. UUIDs, timestamps, and lat/long are acceptable inputs for these fields (respectively) but so are descriptions like 'that time we went to the waterpark in the mall', 'last tuesday' or 'that awesome coffee shop downtown'. These will find appropriate memories to reference.

### Episodic Format
```yaml
- uuid: f0c903be-b00a-4c9d-b984-dc8d0af3c899
  summary: Brief description mainly used for documentation
  keywords: [list of, concepts, to reference]
  createTime: When the memory was created
  duration: Subjective duration of the given episode (optional)
  previous: A memory reference that immediately precedes this one (optional)
  next: A memory reference that immediately follows this one (optional)
  references:
    - List of memory references
    - that this one is tied to
    - in some other way
  content: >
    What is the memory about? This can be as simple or as detailed as necessary.
    The most effective episodic memory content includes information for all the
    senses involved, as well as thought and emotional content.
```

### Procedural Format
*TODO*

### Semantic Format
*TODO*

### Working Memories
*TODO*

Personality
-----------
*TODO*

Hardware
--------
*TODO*

Command-Line Tools
------------------
*TODO*

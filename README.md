# Git primer

![Basic workflow](./images/basic-remote-workflow.png)

Git is a D-VCS or Distributed Version Control System, used mainly by developers to synchronise and share the codebase of a specific project or software.
It allows developers to work simultaneously without stepping on each other toes and merge their work highlighting and handling conflicts. It also allows to keep a record of all the changes on the code.

Every developer works on a local copy of the repository which gets synchronised to a remote location.
Only specific git operations allow to interact with the remote repository (`clone`, `fetch`, `pull`, `push`) whilst the majority of the git operations require no connection to the remote end.

Enterprise platforms (such as GitHub, GitLab, Bitbucket) have been built around git and they not only provide a versioning system but also a collaboration suite that allows developers and system administrators to apply permissions, policies as well as providing tools and constructs that improve the developers' experience.
For instance, GitHub provides issues, pull requests, integrated CI/CD, artifact repository.

## Download

Git is a platform which comes with a command line that is available at [git-scm.com](https://git-scm.com/downloads) or via the package manager of each of the main operating systems.
Several GUI clients are available too, as well as plugins for development IDEs or text editors such as Visual Studio Code.

## Concepts

Git organises data in a hierarchical fashion, so a git repository can be seen as a tree (or a directed graph with no loops).
The 

* **commit**: a commit is an atomic piece of information stored on git. It can bundle several files and represents a point in time that developers can check out at any moment. It represents a node in the tree. Commits can have up to two parents, except for the initial commit that has none.
* **branch**: a sequence of commits, used for allowing multiple development paths and a very granular control over the code that gets released.
* **tag**: tags are mnemonical labels that get assigned to commits (which are identified by a sha1 string). They're tipically used for versioning purposes (i.e. `v1.2.3`).
* **HEAD**: when browsing a git tree, the HEAD points to the commit I'm currently viewing.
* **origin**: by default, the remote repository is identified as `origin`. It's possibile to have multiple remotes though, each one identified by a different name. This allows to keep multiple remote repositories in sync or even to push different branches to different locations from the local repository.


## Basic commands

ALl the commands have several modifiers (flags) that can deeply customise the behaviour.
They can be listed appending the `--help` (or `-h`) flag to the command.
Some commands make sense only when the connection to the remote repository is available, those are the ones marked as `remote`.

### `init`

The `init` command initialises a local empty repository that can be successfully connected to a remote git system.

### `clone` (remote)

Clones the remote repository into the local filesystem.
It can do a full clone as well as a shallow clone, getting just the last n commits.
The latter can be useful in particular situations where only the latest commit is actually needed (i.e. CI/CD scenarios).

### `checkout`

The `checkout` command moves the git HEAD within the git repository.
It accepts either commit SHA-1 hashes, tags or branch names: the latter means the tip of the branch, which is the last commit on it.

### `add`

The `add` command adds one or more files to the staging area, in preparation for a commit.

### `commit`

Creates an actual commit, which is an entry on the git tree that stores all the differences from the parent commit.
Commits are identified by their SHA-1 hash and report an author name and its email address, that can be freely set by the committer.
However, as a security measure, to ensure that the author is really who she claims to be it is possible to sign the commit via PGP.
Some platforms allow to specify that only signed commits be allowed to be pushed to specific branches.

### `fetch` (remote)

Fetches the metadata about the branch from the remote repository without actually getting the changes.

### `pull` (remote)

Pulls the changes from the remote incorporating them into the local repository.
This command can use different strategies depending on git's configuration and CLI modifiers and the behaviour can be radically different from strategy to strategy.

### `push` (remote)

Pushes the local changes to a remote location.
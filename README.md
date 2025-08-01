# Setup (Arch)
TODO: recount setup in steps used with unsuccessful attempts and their resolutions
- Links
    - Operating Systems: Three Easy Pieces book: https://pages.cs.wisc.edu/~remzi/OSTEP/#book-chapters
    - OSTEP Homework repo: https://github.com/remzi-arpacidusseau/ostep-homework
    - OSTEP Projects repo: https://github.com/remzi-arpacidusseau/ostep-projects
    - riscv-gnu-toolchain: https://github.com/riscv-collab/riscv-gnu-toolchain
    - xv6-riscv: https://github.com/mit-pdos/xv6-riscv/tree/riscv
1. Clone the homework repo:
    - `git clone https://github.com/remzi-arpacidusseau/ostep-homework`
2. Clone the projects repo:
    - `git clone https://github.com/remzi-arpacidusseau/ostep-projects`
    - this repo contains INSTALL-xv6.md with instructions for setting up the environment, suggesting use of the `i386-elf-gcc` cross-compilation toolchain, the next repo cloned, `riscv-gnu-toolchain`, is the currently maintained cross compiler that's compatible with the rest of this setup
3. Ensure QEMU is installed: https://wiki.archlinux.org/title/QEMU
    - `sudo pacman -Syu qemu-full`
4. Clone the riscv-gnu-toolchain repo:
    - **WARNING: This is an ~7GB clone**
    - `git clone https://github.com/riscv-collab/riscv-gnu-toolchain`
    - Prerequisites:
        - `sudo pacman -Syu curl python3 libmpc mpfr gmp base-devel texinfo gperf patchutils bc zlib expat libslirp`
        - configuration options near the top of the README in this repo will tempt you, but you can save compilation time and get the `softmmu` support you require with:
            - `sudo pacman -Syyu python-pyelftools python-sphinx python-sphinx_rtd_theme ninja`
            - `./configure --enable-qemu-system --prefix=/opt/riscv`
            - `make build-sim SIM=qemu`
        - Continue the README from "Test Suite" for testing and troubleshooting at compile time
5. Clone the xv6-riscv repo:
    - `git clone https://github.com/mit-pdos/xv6-riscv/tree/riscv`
    - `cd xv6-riscv`
    - VIM cheat sheet: https://www.vim.page/vim-commands-cheat-sheet
    - `vim Makefile`
    - `/CPU` to find the occurence of CPU
    - update `CPUS :=1`
    - `make qemu`
6. Best of luck!

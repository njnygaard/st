# My Changes to AUR st

2023-09-07T21:00:53-0700

I wanted to capture the workflow because it was the first time I modified a package before installing it.

```bash
# Go get it from the AUR
git clone https://aur.archlinux.org/st.git
cd st
# Build it without installing
makepkg --nobuild
# Patch with stuff from https://st.suckless.org/patches/
cd src/st-0.9
patch -i ~/Downloads/st-scrollback-0.8.5.diff
patch -i ~/Downloads/st-colorschemes-0.8.5.diff
# Pop back
...
# Make it as an Arch package
makepkg --noextract --install
# Try it out
st
# Make additional changes
rm -rf pkg st-0.9-4-x86_64.pkg.tar.xz
vi src/st-0.9/config.h
# Reinstall
makepkg --noextract --install
st
# Add another remote
git remote add personal git@github.com:njnygaard/st.git
git branch -M main
git push -u personal main
git add .
git commit -m"scrollback and colorschemes"
git push personal main
```

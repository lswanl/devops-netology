1.  git show aefea 
commit aefead2207ef7e2aa5dc81a34aedf0cad4c32545 
Author: Alisdair McDiarmid <alisdair@users.noreply.github.com> 
Date: Thu Jun 18 10:29:58 2020 -0400 

Update CHANGELOG.md 
 

2. git show 85024d3
  commit 85024d3100126de36331c6982bfaac02cdab9e76 (tag: v0.12.23)

3. git show --pretty=format:' %P' b8d720^
58dcac4b798f0a2421170d84e507a42838101648 ffbcf55817cb96f6d5ffe1a34abe963b159bf34e

4. git log v0.12.23..v0.12.24 --oneline 
33ff1c03b (tag: v0.12.24) v0.12.24 
b14b74c49 [Website] vmc provider links 
3f235065b Update CHANGELOG.md 
6ae64e247 registry: Fix panic when server is unreachable 
5c619ca1b website: Remove links to the getting started guide's old location 
06275647e Update CHANGELOG.md 
d5f9411f5 command: Fix bug when using terraform login on Windows 
4b6d06cc5 Update CHANGELOG.md 
dd01a3507 Update CHANGELOG.md 
225466bc3 Cleanup after v0.12.23 release 

5. git log -S'func providerSource' --oneline 
5af1e6234 main: Honor explicit provider_installation CLI config when present 
8c928e835 main: Consult local directories as potential mirrors of providers

6. git log -S'globalPluginDirs' --oneline 
35a058fb3 main: configure credentials from the CLI config file 
c0b176109 prevent log output during init 
8364383c3 Push plugin discovery down into command package

7. git log -S'func synchronizedWriters' --pretty=format:'%h - %an %ae' 

bdfea50cc - James Bardin j.bardin@gmail.com 
5ac311e2a - Martin Atkins mart@degeneration.co.uk
 
 
  

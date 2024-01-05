# A [Giter8][g8] / [SBT][sbt] / [Scala][scala] / [Nix][nix] / [Flake][flake] template

A Giter8 template for a fully configured Scala SBT single but multibuild ready project. It is configured in a slightly opinionated but mostly dependency free fashion.

All versions will always stay hardcoded as opposed to being chooseable or automatically updatable via Giter8 in order to guarantee the soundness of the build. In other words, assuming you don't have any global settings/plugins the build won't break unless you manually break it by changing versions by hand. Enjoy!

1. Run the following sbt command to create a scala 2 project
```bash
sbt new pradeepcheers/scala2-seed.g8  # for Scala 2
```
or

2. If giter is installed the following command can be used instead
```bash
g8 pradeepcheers/scala2-seed  # for Scala 2
```
3. The result will look something like this, you can set the project, package and the organization name
```
$ sbt new pradeepcheers/scala2-seed.g8
[info] welcome to sbt 1.7.0 (Oracle Corporation Java 18.0.2)
[info] loading settings for project global-plugins from macbook-pro-m1-settings.sbt ...
[info] loading global plugins from /Users/psy03/.sbt/1.0/plugins
[info] set current project to new (in build file:/private/var/folders/r5/1_2_s2fs41b0cmswvd6rd03r0000gp/T/sbt_e5d8a475/new/)
SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
SLF4J: Defaulting to no-operation (NOP) logger implementation
SLF4J: See http://www.slf4j.org/codes.html#StaticLoggerBinder for further details.
A Giter8 template for a fully configured Scala sbt project.

name [sample-project]: some-project
organization [com.sample.project]: some-org
package [any-org]: some-pkg

Template applied in /Users/xxx/path/./some-project
```
4. Run the following command to open the project created using [Codium](https://vscodium.com/) 
```
cd some-project
codium .
```
5. Direnv needs permission, `.envrc` is blocked by default, execute `direnv allow` to approve the contents of `.envrc`.

6. Nix flake is used setup the scala environment. Make sure that Nix is installed on your machine. At the moment java version is hardcoded to openjdk java 11.0.21. Java version can be changed in flake.nix and pkgs.nix before running the following command.
```
nix flake check

nix develop
```
7. Following command can be used to see all the 
```
echo -e ${buildInputs// /\\n} | cut -d - -f 2- | sort
```

  If the installed path needs to be displayed then 
```
echo -e ${buildInputs// /\\n} | sort -t- -k2,2 -k3,3
```

  Shows everything Nix put on the path
```
echo $PATH | sed 's/:/\n/g' | grep /nix/store | sort --unique -t- -k2,2 -k3,3
```
8. This is a sbt project, start sbt on the terminal to run or test the project
```
sbt
```

[g8]: http://www.foundweekends.org/giter8/
[sbt]: https://www.scala-sbt.org/
[scala]: https://www.scala-lang.org/
[nix]: https://nixos.org/learn
[flake]: https://nixos.wiki/wiki/Flakes

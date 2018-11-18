# ScalaSnippets


Scala Standard Library:
https://www.scala-lang.org/api/current/index.html



Scala Scheatsheet
https://github.com/danielsef/progfun-wiki/blob/gh-pages/CheatSheet.md



SBT uses the same directory structure as Maven for source files by default (all paths are relative to the base directory):
src/
  main/
    resources/
       <files to include in main jar here>
    scala/
       <main Scala sources>
    java/
       <main Java sources>
  test/
    resources
       <files to include in test jar here>
    scala/
       <test Scala sources>
    java/
       <test Java sources>
Other directories in src/ will be ignored. Additionally, all hidden
directories will be ignored.




SBT
  - compile
  - test
  - run


Dependencies:

Warning: the scala version shown in this screenshot is 2.10.3 and it's outdated. The scala version that we will use for this course is 2.11.x. Also, note that the scalatest dependency has the scala version embedded in "scalatest_2.10" and that there's no `2.0` version for 2.11.x. So, replace:
  libraryDependencies += "org.scalatest" % "scalatest_2.10" % "2.0" % "test"

by:
  libraryDependencies += "org.scalatest" % "scalatest_2.11" % "2.2.6" % "test"
  libraryDependencies += "org.scalatest" %% "scalatest" % "2.2.6" % "test"

The double percentage symbol will force sbt to use the current scala version defined in scalaVersion (which has to be "2.11.7" or "2.11.8").



Organizing the build
  https://www.scala-sbt.org/0.13/docs/Getting-Started.html
  https://www.scala-sbt.org/0.13/docs/Organizing-Build.html



SBT: Rerun Tests
  One of the coolest features of sbt is that it can rerun your tasks without manual intervention whenever any project source file changes. This is enabled using the ~ operator. If you prefix any sbt task with ~ then sbt will wait for changes in the source files. As soon as any file changes, it will rerun that task.

  Type the ~test command inside sbt shell:

  > ~test




Tip: Getting the right Scala version with %%
    As mentioned before Scala remain binary compatible only between minor versions. This results in various library versions for different scala versions. Few sections back, we used scalatest library. The dependency was defined as follows:

    libraryDependencies += "org.scalatest" % "scalatest_2.11" % "2.2.6" % "test"
    The scala version was specified in the artifactID "scalatest_2.11". This means every time we update the Scala version we would have to update the dependency. We can implicitly get the Scala version using the %% operator:

    libraryDependencies += "org.scalatest" %% "scalatest" % "2.2.6" % "test"



Tip: Pass options to Scala compiler
  You can pass options to scalac by defining a setting scalacOptions as shown below:

  scalacOptions ++= Seq("-feature", "-language:_", "-unchecked", "-deprecation","-encoding", "utf8")


S-99: Ninety-Nine Scala Problems:
http://aperiodic.net/phil/scala/s-99/

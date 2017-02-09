Readable-stream API for Scala.js
================================
This is a Scala.js type-safe binding for [Readable-stream](https://www.npmjs.com/package/readable-stream)

A Streams3, a user-land copy of the stream library from Node.js

#### Build Dependencies

* [ScalaJs.io v0.3.x](https://github.com/ldaniels528/scalajs.io)
* [SBT v0.13.13](http://www.scala-sbt.org/download.html)

#### Build/publish the SDK locally

```bash
 $ sbt clean publish-local
```

#### Running the tests

Before running the tests the first time, you must ensure the npm packages are installed:

```bash
$ npm install
```

Then you can run the tests:

```bash
$ sbt test
```

#### Examples

```scala
import io.scalajs.nodejs.buffer.Buffer
import io.scalajs.nodejs.process
import io.scalajs.npm.readablestream.Readable

val bulk = new Readable()
bulk._read = () => {}

('A' to 'F') foreach { ch =>
  bulk.push(Buffer.from(String.valueOf(ch)))
}
bulk.push(null)
bulk.pipe(process.stdout)
```

##### Output:
```text
ABCDEF
```

#### Artifacts and Resolvers

To add the Moment binding to your project, add the following to your build.sbt:  

```sbt
libraryDependencies += "io.scalajs.npm" %%% "readable-stream" % "2.2.2"
```

Optionally, you may add the Sonatype Repository resolver:

```sbt   
resolvers += Resolver.sonatypeRepo("releases") 
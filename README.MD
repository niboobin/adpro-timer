![Timer](https://cdn.discordapp.com/attachments/314315831465213953/1235840362132803635/image.png?ex=6635d587&is=66348407&hm=91acbc3115aecda3ff84714ccecce8b70c09e126736ba6b369fd941abc26aae3&)

The line `Obin's Computer: hey hey` is printed first because the `println!("Obin's Computer: hey hey");` statement is executed immediately in the main function, while the `println!("Obin's Computer: howdy!");` and `println!("Obin's Computer: done!");` statements are inside an asynchronous task that is spawned to run concurrently.

![Replicate](https://cdn.discordapp.com/attachments/314315831465213953/1235849003887755297/image.png?ex=6635dd93&is=66348c13&hm=083bb854d2817e06677dcb3ba0b5df029556e9938c724dffce8f23b4280945b6&)

If we replicate the spawner.spawn block and run it, two asynchronous tasks will be created.
However, because these tasks are asynchronous and run concurrently, the exact order of the output might vary. It's possible that one task might start and finish before the other.

![Replicate2](https://cdn.discordapp.com/attachments/314315831465213953/1235891428396367892/image.png?ex=66360516&is=6634b396&hm=30a0c7b1d416eefafe1fe319f0fa742fe396c2564ee90602a5f29175dacf69c0&)

If we remove the `drop(spawner)` line and run the program, the executor might keep waiting for new tasks to be spawned indefinitely, causing the  program to hang or deadlock. But now the order of the output will be proper.
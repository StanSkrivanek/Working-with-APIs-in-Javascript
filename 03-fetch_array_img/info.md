[Using `for...of` instead `forEach` in **async/await**](https://stackoverflow.com/questions/37576685/using-async-await-with-a-foreach-loop)

Sure the code does work, but I'm pretty sure it doesn't do what you expect it to do. It just fires off multiple asynchronous calls, but the printFiles function does immediately return after that.

**Reading in sequence**

If you want to read the files in sequence, you cannot use forEach indeed. Just use a modern for … of loop instead, in which await will work as expected:

```js
async function printFiles() {
  const files = await getFilePaths();

  for (const file of files) {
    const contents = await fs.readFile(file, "utf8");
    console.log(contents);
  }
}
```

**Reading in parallel**

If you want to read the files in parallel, you cannot use forEach indeed. Each of the async callback function calls does return a promise, but you're throwing them away instead of awaiting them. Just use map instead, and you can await the array of promises that you'll get with Promise.all:

```js
async function printFiles() {
  const files = await getFilePaths();

  await Promise.all(
    files.map(async (file) => {
      const contents = await fs.readFile(file, "utf8");
      console.log(contents);
    })
  );
}
```

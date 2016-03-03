# Ember-build-prod-test

This example project is an attempt to verify what I am seeing in a production app I am involved in building at present. As soon as I attempted to install TinyMCE within that project the build times increased massively.

I am using Broccoli Funnel to pull in the files I need from the TinyMCE bower lib in `ember-cli-build.js`.

To illustrate this, I have set up two commands: `npm run build:prod` and `npm run build:prod:tinymce`. The second is the same as the first except that it sets a flag to enable the funnelling of TinyMCE in `ember-cli-build.js`.

If you `npm run build:prod` you'll see a lot of console output. When it completes, you can see the time that it took in the final output.

The time difference between `npm run build:prod:tinymce` and `npm run build:prod` is significant on my system.

### My setup:

System info
* Model Name: MacBook Pro
* Processor Name: Intel Core i5
* Processor Speed:  2.4 GHz
* Number of Processors: 1
* Total Number of Cores:  2
* L2 Cache (per Core):  256 KB
* L3 Cache: 3 MB
* Memory: 16 GB

Hard Disk info:
* Device Name:  APPLE SSD SD0256F
* Media Name: APPLE SSD SD0256F Media
* Size: 250.14 GB (250,140,434,432 bytes)
* Medium Type:  SSD

Node info:
`npm -v`: 2.14.21
`node -v`: v4.3.1

### Times:
* `npm run build:prod:tinymce`: ~4.5 min
* `npm run build:prod`: ~15 sec

The main issue seems to happen immediately after this point in the build:
```
  broccoli-merge-trees:TreeMerger (allTrees) build:
 { count: 1, in: '12ms', mergeTime: '0ms', applyPatchTime: '12ms', treeTime: '0ms', entries: 7, indices: 7, overwrite: true } +0ms
```

In both cases the build appears to hang for a period of time at this point, but in the `build:prod:tinymce` version it hangs for a *much* longer time.


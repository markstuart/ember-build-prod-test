# Ember-build-prod-test

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

Times:
* `npm run build:prod:tinymce`: `real 4m44.138s`
* `npm run build:prod`: `real 0m30.193s`

The main issue seems to happen at this point in the build:
```
  broccoli-merge-trees:TreeMerger (allTrees) build:
 { count: 1, in: '12ms', mergeTime: '0ms', applyPatchTime: '12ms', treeTime: '0ms', entries: 7, indices: 7, overwrite: true } +0ms
```

In both cases the build appears to hang for a period of time at this point, but in the `build:prod:tinymce` version it hangs for a *much* longer time.


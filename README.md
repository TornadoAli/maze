# TypeScript Maze

### Background
I am writing this as a learning exercise for myself in trying to understand TypeScript and its benefits, whilst having an interesting problem to use as an example.

### Getting it running
It is intentionally a very simple App. I have been running it locally on my Mac through Apache Web Server, and using the TypeScript compiler (tsc) to transcompile the TypeScript into the JavaScript that actually runs on the browser.

### Browser support / testing
Note that as this has mostly been a way for me to learn TypeScript (rather than an operational product!) I've only been testing this on Chrome on my Mac. If it doesn't work on your browser then let me know and I'll try to fix it if I can.

### Issues / Selected To Dos
* I haven't completely finished added in all Types from when I re-wrote this from pure JavaScript. Should be finished soon.
* Note that there is a bit of a hack when it comes to the way the 'recursive backtracking' algorithm is being displayed. Specifically I'm referring to the fact that in the original JavaScript I simply added a couple of new properties to a couple of objects - 'robotVisited' and 'lineDrawn' to the cell objects and 'line' to the displayCell (HTMLTableCell) object. This is fine in the loose world of JavaScript, but in TypeScript it causes 'errors' when you compile to JavaScript using tsc. See the section below. Note that these errors don't actually cause any problems in running the app, but do probably indicate that a bit of a refactor is needed!
* I'm not entirely happy with the relationship between maze, robot and robotAlgorithm objects - they could be better decoupled so I'm going to give this some thought.
* Could possibly do with a new class that is an abstract child of MazeViewer and serves as an abstract Parent class of BorderMazeViewer, CompositeImageMazeViewer and ImageMazeView as these all use HTML tables and it could reduce code duplication. I'm going to work on this.

### Expected errors on using 'tsc' to compile the TypeScript into JavaScript
See section above for background. Note that these errors don't actually stop the app from working. I will work to refactor the TypeScript code to remove these.

1. ts/robot/recursiveBacktrackingRobotAlgorithm.ts(26,20): error TS2339: Property 'robotVisited' does not exist on type 'Cell'.
2. ts/robot/recursiveBacktrackingRobotAlgorithm.ts(35,21): error TS2339: Property 'lineDrawn' does not exist on type 'Cell'.
3. ts/robot/recursiveBacktrackingRobotAlgorithm.ts(38,21): error TS2339: Property 'lineDrawn' does not exist on type 'Cell'.
4. ts/robot/recursiveBacktrackingRobotAlgorithm.ts(69,32): error TS2339: Property 'robotVisited' does not exist on type 'Cell'.
5. ts/robot/recursiveBacktrackingRobotAlgorithm.ts(72,31): error TS2339: Property 'lineDrawn' does not exist on type 'Cell'.
6. ts/viewers/borderMazeViewer.ts(70,29): error TS2339: Property 'line' does not exist on type 'HTMLTableCellElement'.
7. ts/viewers/borderMazeViewer.ts(77,12): error TS2339: Property 'lineDrawn' does not exist on type 'Cell'.
8. ts/viewers/borderMazeViewer.ts(78,28): error TS2339: Property 'line' does not exist on type 'HTMLTableCellElement'.
9. ts/viewers/borderMazeViewer.ts(80,28): error TS2339: Property 'line' does not exist on type 'HTMLTableCellElement'.
10. ts/viewers/borderMazeViewer.ts(93,17): error TS2339: Property 'line' does not exist on type 'HTMLTableCellElement'.


### Original JavaScript source
I originally wrote this in JavaScript and the later re-wrote it in TypeScript. I wanted to learn about OO in JavaScript first before I tried it in TypeScript so that I could better appreciate what TypeScript does, and the benefits it brings. The JavaScript source then became out-of-date as I worked only on the TypeScript version, so it is no longer part of the repo, but for interested parties it can still be found in earlier commits.

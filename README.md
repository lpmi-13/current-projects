# current projects

```
# copyright Pete Langley 2018
#
# don't have more than three things on the go at once
```

## 3) AWL/AVL vocab API
\# open question as to whether we need an API to just send back 
\#the lists? Maybe do this after we have the application that uses 
\#the data...
\# also, do we actually want to integrate catvar data in this?

- script out expansion (XX, XXS) => { NN/VBP, NNS/VBZ }
- script out mapping from finer POS tags to course tags (VBP,VBG,VB,VBZ) => (V)
- need a backend to store the data (depending on structure, may
prefer postgres as we want relations) 
- MVP of the quiz is academic texts with certain words (from AWL) removed to be replaced by the users (cloze test)
- needs to be manually re-coded for words that span classes (stress --> NN/VB)
- second stage MVP might be to combine the data, and not differentiate between the original list
differences...possibly yield a higher dataset (since we're not concerned with the word counts
for this particular app)
- eventually would be nice to track logins and aggregate progress


#############################################################
#############################################################
#############################################################

## 8) Parson Problems
- start with python and javascript
- need MVP with three different ones to present in a frontend
- need to give feedback on whether successfully reordered or not

## 4) put up factor10 to a factor of 10 (potentially just make a
factor10 generator that takes any site and increases everything by
10 times)

## 5) minimals
- use youtube data api to get data for the whole channel
-need to revamp the processing pipeline to garbage collect after the conversion is done, also to stop and clean up after 100(?) videos have been processed.
- need to update pipeline to only care about vowels

## 6) React Native shaker App
- need a proof of concept hello world made and installing on a 
local device
https://medium.com/react-native-training/using-sensors-in-react-native-b194d0ad9167
- need a list of words (2-syllable, alternating stress)
- game with shaking based on the stress patterns on 10 of these words

## 7) BrokeRobot shirts
- need to get more source data across different genres
(poetry, math, literature, history, politics, media, etc)
- need to train models for each of these
- need to filter out the translations for stopwords
- need to output a whole bunch of these into a DB

## 9) Stress Maze
- need a list of words (both general and academic lists) of 2/3/4
syllables. The list needs to be filterable on number of syllables
as well as which syllable has the primary stress (there could be two stresses for 4-syllable words, so possible major and minor stress)
- need a way to procedurally generate a path through squares in a
react UI (MVP is squares, eventually we do hexagons)
- need to map the stress patterns onto these hexagons

## 10) Pypobot
- add in tests for the bare minimum NLP module:
  ...first just check for duplicated strings, then misspellings, then dependency parse issues...
  (mock this with sample texts with known numbers of "discoverable"
  errors...first text only has first type of error, second text
  has first and second, usw...)
- need to refactor to allow user to type in text for replacements as opposed to pure string replacement
- need to perform extended error checking in each readme instead of only checking for hardcoded error

## 11) CodeReader
- start with python
- need to grab the repos for the top 100 starred projects on github
- need to get data on cyclomatic complexity of each on different
levels
(repo level, file level, function level)
- need to grab data on language these repos/files are in
- need a frontend to filter on both level/language
- possibly also add in line density for functions?

## 12) Desktop thesis helper
- need to get a corpus of academic english to compute stats for
(average usage of each word...in vector format?)
- wrap in electron
- package for Windows/Mac/Linux
- output whether the terms in the analyzed paper fall far from the average stats for each token
- output outliers for sentiment in terminology (possibly tailor for US-UK english)
- collate and output stats for baselines based on papers scraped off Arxiv?

## 1) classroom-css
- have a local app with the CFG html and css running
- have a docker container that can mount the files in a volume
- need ngrok to tunnel out from the dev server in the docker container to the public internet
- need a good readme for it

## 15) Update Rebasic
- check expected file sha1 hashes as well as commit presence

## 16) Write tests for all React projects

## 17) Rewrite previous projects in React
- AnTweet
- AnRedd
- AnWriting?

## 18) Deploy static apps just from Nginx
- Touchwords
- SentenceFactory
- AnRedd (once backend is dockerized)
- AnTweet (frontend)

## 19) Audit all sites for security
- Server-side enforcement of type/length for inputs
(AnTweet, AnWriting, Convohelper, Github User Stats,
Micromaterials-API, derivations-API, avl-API)
- HTML escape before putting search results on page?
- Update content security policy to most locked down that doesn't break the site (JS at minimum)
- check all server response content headers (utf-8, application/json, encoded as json)
- check all FE requests that put values into the URL params...if there are any, URL escape them first
- make sure none of the GET requests have side-effects
- Add middleware sanitizers to express/flask apps
- Update permissions for all application servers to run as non-root users

## 20) Audit all sites for Accessibility/UX
- Fix contrasts, add alt tags to every image
- Add custom 4XX/5XX error pages

## 21) Dockerize backends of existing apps
- AnRedd
- AnWriting
- SentenceFactory

## 22) What to Expect when you're Expect-ing
- simple static page that shows which APIs go with which
JS assertions library (chai/expect/enzyme/etc)

## 23) CBMC in Docker container
- need to test form of inputs/outputs
- programmatically remove particular methods and ask the user
to write a method to replace it...give feedback on whether the
user's method "functions the same"

## 24) Investigate logging on githubuserstats

## 26) Content security policy in nginx (script-src)
- grammarbuffet, done
- micromaterials, outstanding
- statsbuffet, done 

## 28) Ensure names and styles in python projects adhere to PEP8

## 29) Set `NODE_ENV=production` in all node-backed apps

## 30) Turn Stress in the Speech Stream into a Python module to take in a word and output the reasons why it has a given pronunciation
- key syllable
- prefixes
- affixes
- origin of the root

## 31) Update Nginx configs to use proxy_pass instead of rewrite

## 2) Github User Stats
- add ability to run in dev mode with docker (v2)
- update data pipeline to use the gharchive json dumps (v2)
- add a User screen returning a user view for the clicked user (v2)
- update data ingested to store every repo merged into (v2)
- add an Add screen with the ability to enter a user to add to the list (for both original and updated list) (v3)

## 32) Run images through optimizers
- grammarbuffet
- lpmi-13.github.io

## 33) Add Minimals to portfolio

## 34) PWA box grid game with preact & CSS Grid
- https://hackernoon.com/how-to-create-a-pwa-game-using-preact-in-5-steps-tutorial-c8b177037c80

## 35) test out AR with react web app
- https://github.com/nitin42/React-Web-AR

## 36) mock out turning a github user's contribution data into a sim-city web UI
- each programming language is a type of zone (commercial, industrial, residential...possibly map to compiled vs scripting vs ??? languages)
- height is based on number of merged PRs
- density is based on chronology?
- area is based on number of repos contributed to

## 37) Attempt to redo text highlighting in textarea
- https://github.com/keustma/react-highlighted-textarea

## 38) Git micromaterial about reflog

## 39) rap poetry mashup
- get source for shakespeare at poetrydb.org
- http://poetrydb.org/author/shakespeare/title (all titles endpoint)
- http://poetrydb.org/title/A%20Lover's%20Complaint (title endpoint)
- use Genius API (with python wrapper) to get rap lyrics
- get all shakespeare, then compute number of words to get a balanced
sampling by normalizing the same number from other rappers we wanna mashup
- DON'T FORGET TO REPLACE THE BAD WORDS!!!

## 40) Command line sentence parser
- start with parse trees
- look at the source code for ascii art generators in python
- possibly also linux package?
- v2 is a full dependency parse

## 41) Add reflog-power to portfolio

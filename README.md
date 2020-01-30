# current projects

```
# copyright Pete Langley 2018
#
# don't have more than three things on the go at once
```
## 70) Blog post about using TTS to automate micromaterials in a foundations ESL course

## 73) estimate AWS costs of different infra configs
- follow https://medium.com/@bjorn_248/estimating-aws-infrastructure-cost-from-terraform-templates-307fae53e4bd
- possibly pull everything into one repo
- at the very least have some sample exercises that can be run against an existing AWS cloud environment

## 3) AWL/AVL vocab API
\# open question as to whether we need an API to just send back 
\#the lists? Maybe do this after we have the application that uses 
\#the data...
\# also, do we actually want to integrate catvar data in this?

- script out expansion (XX, XXS) => { NN/VBP, NNS/VBZ }
- script out mapping from finer POS tags to coarse tags (VBP,VBG,VB,VBZ) => (V)
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
- possibly use https://github.com/Hellenic/react-hexgrid
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
- especially a11y tests with cypress

## 17) Rewrite previous projects in React
- AnTweet
- AnRedd
- AnWriting?

## 18) Deploy static apps just from Netlify
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
- Add labels for all inputs
- make sure all frontends have cypress a11y tests

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

## 26) Content security policy in nginx (script-src)
- micromaterials, outstanding
- statsbuffet, done 

## 28) Ensure names and styles in python projects adhere to PEP8

## 29) Set `NODE_ENV=production` in all node-backed apps

## 30) Turn Stress in the Speech Stream into a Python module to take in a word and output the reasons why it has a given pronunciation
- key syllable
- prefixes
- affixes
- origin of the root

## 2) Github User Stats
- possibly do all this via gatsby and generate a page per search result?
- add ability to run in dev mode with docker (v2)
- update data pipeline to use the gharchive json dumps (v2)
- add a User screen returning a user view for the clicked user (v2)
- update data ingested to store every repo merged into (v2)
- add an Add screen with the ability to enter a user to add to the list (for both original and updated list) (v3)


## 35) test out AR with react web app
- https://github.com/nitin42/React-Web-AR

## 36) mock out turning a github user's contribution data into a sim-city web UI
- each programming language is a type of zone (commercial, industrial, residential...possibly map to compiled vs scripting vs ??? languages)
- height is based on number of merged PRs
- density is based on chronology?
- area is based on number of repos contributed to

## 37) Attempt to redo text highlighting in textarea
- https://github.com/keustma/react-highlighted-textarea


## 40) Command line sentence parser
- start with parse trees
- look at the source code for ascii art generators in python
- possibly also linux package?
- v2 is a full dependency parse


## 42) Academic corpus to analyze form/function stuff
- how are writers critiquing existing research
- how are writers hedging
- what is the frequency distribution of adverbials (compare/contrast, order, frequency, etc)
- what is the order of clauses, and how is this related to the discourse structure of the arguments/claims made


## 44) Use pre-computed word vectors to highlight weird/unexpected word usage
- try with both ELMo and FastText vectors
(are vectors/embeddings the best way to check this? We essentially just need contextualized word information for the same word across two corpora)
- do the same, but with Bert
- need a semi-mid sized corpus to investigate (github readme corpus?)

## 47) Use the Youtube API to pull in a rap song lyrics video
- display predicted stress pattern for lyrics
- possibly grab these lyrics from the genius API?
- MVP might be predicting based on content/function words
- Eventually want a system that combines auditory data from the actual songs with NLP-based stress prediction algorithms

## 48) See if any alternate patterns are appropriate for the service workers
- network then cache for everything?
- never cache for sw, always cache for others?

## 49) Create simple micromaterials for call/bind/apply

## 50) Make a gatsby site for https://github.com/florinpop17/app-ideas

## 51) Compare spoken interview prep to "average" developer corpus
- train speech-to-text model for one specific user
- user speaks in response to written prompts for common interview questions
- collect corpus of developer podcasts (possibly cluster by topic/level?)
- compare lexico-grammatical features of user's response to features of the corpus
(vocabulary, lexical density, length of response (applicable?), expected frequency counts for common terms (data, function, etc?), amount of subordinate structure...
- compare suprasegmental features of user's response to corpus (feasible?)
(intonation patterns, speed of response, stress patterns (these should be predictable at the word level perhaps)


## 53) Browser-based micromaterial to test out async promise strategies

## 54) Create spectrogram analysis to identify stress/pitch/volume
- can we get this information from spectrograms of words? (probably not)
- can we get this information from spectrograms of longer phrases? (maybe)
- can we just mark where these peak a certain delta above the mean? (definitely)
- can we then use those data points to train a system to identify the stresses
in an extended audio sample? (interesting question)
- eventually we could just use that to create a mobile app the vibrates along
with the stress in a TED talk in a mobile app (react native, naturally!)

## 55) Create a testing framework to demonstrate good/bad tech interview questions
- is the question (either in F2F interview or tech test) testing what you think it is?

## 56) Create corpus of "dev talk" from podcast transcripts
- Find good representative dev podcasts (probably FE to start)
- write script to get transcripts (and possibly audio as well)
- Create corpus of "dev talk"

## 57) Recreate CV in HTML with Gatsby

## 60) Use vector comparison to find poorly written exam distractors
- maybe BERT would be better for this, not sure
- get data set of exams with questions/distractors
- is it possible to get a data set with item analysis and also data on which
questions students got correct/incorrect?

## 61) Even simpler IP and Bitmask slider visualization
- 255.255.248.0   in binary: 11111111 11111111 11111000 00000000
                           -----------------------------------
                           I counted twenty-one 1s             -------> /21
- make a slider UI and just update the values as the user slides the values
to the left or right (probably put the click handler on the entire div
- possibly add feature to update the network address as the values change:
128.42.5.4      in binary: 10000000 00101010 00000101 00000100
255.255.248.0   in binary: 11111111 11111111 11111000 00000000
                           ----------------------------------- [Logical AND]
                           10000000 00101010 00000000 00000000 ------> 128.42.0.0
- possibly also add feature to calculate broadcast address:
128.42.5.4      in binary: 10000000 00101010 00000101 00000100
Host bit mask            : 00000000 00000000 00000hhh hhhhhhhh
                           ----------------------------------- [Force host bits]
                           10000000 00101010 00000111 11111111 ----> 128.42.7.255
- also possibly add calculation of maximum number of hosts in a subnet:
To find the maximum number of hosts, look at the number of binary bits in the host number above. The easiest way to do this is to subtract the netmask length from 32 (number of bits in an IPv4 address). This gives you the number of host bits in the address. At that point...

Maximum Number of hosts = 2\*\*(32 - netmask\_length) - 2

The reason we subtract 2 above is because the all-ones and all-zeros host numbers are reserved. The all-zeros host number is the network number; the all-ones host number is the broadcast address.

Using the example subnet of 128.42.0.0/21 above, the number of hosts is...

Maximum Number of hosts = 2\*\*(32 - 21) - 2 = 2048 - 2 = 2046

- ...I also realize this isn't in any way "simpler", so just do whatever is feasible, based on https://networkengineering.stackexchange.com/questions/7106/how-do-you-calculate-the-prefix-network-subnet-and-host-numbers

## 62) Static app visualizer for whether two hosts are on the same network
- same reference as above, just further down the page

## 63) Browser based interface to give practice solving recursion problems
- good programmers aren't better at this because they're smarter, just because they've had more practice doing it.
- generate 100 or so similar recursion problems (or possibly a new one every hour?) and have users solve it via coding in the UI

## 64) Put the n-gram tracing approach to authorship attribution in a docker container
- possibly put it somewhere behind a web interface where we can fire texts at it?
- use python

## 65) Create a native app to record speech and stretch the octave range
- English usually involves between 2-2.5 octaves in normal conversational speech
- Some cultures don't use very wide octave ranges (whether out of politeness or habit)
- The lack of range can suggest things to English listeners (boredom/disinterest/etc), so should not be unconsciously repeated from 1st culture out of habit.

## 66) Remake the python conversational bot treasure hunt via web interface
- Needs a log in, or no way to remember where the user "left off"
- should be enough to keep the same script and put users into a simple postgres DB
- possibly consider using serverless functions for auth

## 67) App and/or website with peer-reviews simplifications of scientific concepts
- Summaries that are gold standard

## 68) Cards Against How Might We - web app version
- put https://github.com/BethFox/CaHMW online as a webapp

## 69) Test out training Text to Speech Model
- play around with https://github.com/r9y9/wavenet_vocoder to see how much data is needed for a passable TTS model
- possibly get single speaker samples from youtube
- identify costs for running something in the cloud for a unique user

## 71) Investigate ability to automate creation of videos of an automated system creating programming micromaterials
- eg, creating incomplete recursive functions
- then after a time delay, showing the solution
- unclear what other input would be helpful/useful during this visual input...sounds?

## 72) Use Kialo to generate compare/contrast materials
- still need to export discussions manually (boo)
- Kialo-Parser only works with python2 (possibly PR?)
- generate a more robust data structure to ingest into a web app
- create simple web interface to show one argument, and have users select the either a supporting statement or a counterstatement (possibly add adverbial conjunctions?)


## 74) Implement BookFace as a mobile app in React Native
- Facebook, but no data leaves
- A place to write notes in a well-designed format about family/friends
- Set reminders for yourself to send Xmas cards, birthday cards, etc
- Instead of people adding you, only you add people
- Kind of like a digital rolodex

## 75) Collaborate with Julia (B@rk) on using the e-zines to fuel TechEd materials

## 76) Set up static site to track micromaterials on github
- possibly gatsby (needs a search though...)
https://www.gatsbyjs.org/packages/gatsby-plugin-local-search/
https://www.gatsbyjs.org/docs/adding-search-with-js-search/
- use GitHub API to pull down all issues labelled as micromaterials
- filter for bad words

## 77) map out different tech skill areas to target with TechEd
- networking
- security
- a11y
- functions
- design
- vocab
- documentation(?)

## 78) Investigate ways to automate testing with a screenreader
- could we use Speech to Text models to analyze...something...?
- make sure it doesn't read the whole thing at once

## 79) Mock up professional website/blog example
- http://jaspermontana.com/
- try out with gatsby
- choose nice hero image
- include twitter feed on right side
- about/research/media/publications

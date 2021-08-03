# current projects

```
# copyright Pete Langley 2018
#
# don't have more than three things on the go at once
```

# 136) Kubernetes the hard way on Vultr
- similar to linode, most likely

# 122) Micromaterial to visualize placing ECS tasks into instances in a cluster
- make sure the task reservations (CPU/RAM) are variable and also that the VM specs are variable
- probably just drag and drop "taks" into VMs to watch how mismatches might throw specific errors: unable to place task because no container instances met all of its requirements
- see if anyone on awsnewbies or cloudnewbies finds this useful

# 137) Create micromaterial for tcpdump
- possibly related to #130 above, but even just for locally running VMs in a well-defined subnet.
- have a script to pick which of the 3 (or however many) VMs/containers is the "noisy one" and make it quiet down.
- terminal-based micromaterial

---

## 2) Github User Stats

- get something working with github actions to just log the latest in the Purcell/lpmi-13 race for unique repos merged to.
- apparently the API has changed, and the legacy code doesn't work anymore, so this needs to be built from scratch (or at least the issues part)
- https://api.github.com/search/issues?q=type:pr%20is:merged%20author:lpmi-13 still bring back what we want, so might just use that as a workaround, since I'm only doing it for two users, essentially

tech stuff
- possibly do all this via gatsby and generate a page per search result?
- add ability to run in dev mode with docker (v2)

UI stuff
- add a User screen returning a user view for the clicked user (v2)
- show graphic with different sizes spheres representing number of commits per unique repo (eg, pypobot cretes many very small circles)

- add an Add screen with the ability to enter a user to add to the list (for both original and updated list) (v3)

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
- try with GPT-2 (or maybe 3)
https://talkpython.fm/episodes/show/1/eve-restful-apis-for-humans

## 8) Parson Problems
- add javascript option
- add ruby option
- add ability to filter by "complexity" if possible
- get input from the #accessibility channel about how best to make this usable via screen readers
- investigate using JS-based AST parsers in the browser to evaluate the "correctness" of the re-order instead of just the literal order
- investigate only storing the beginning/ending of the function lines from the github source code and using github as an open API to grab this stuff at runtime (disadvantage would be that code changes, though this is also technically an issue if we are storing pointers to line numbers anyway)
- see if there's a way to turn loops (maybe this should be in a different micromaterial) into blocks, as evan suggested.
- bunch of different parsers here: https://github.com/fkling/astexplorer

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

## 28) Ensure names and styles in python projects adhere to PEP8

## 29) Set `NODE_ENV=production` in all node-backed apps

## 30) Turn Stress in the Speech Stream into a Python module to take in a word and output the reasons why it has a given pronunciation
- key syllable
- prefixes
- affixes
- origin of the root


## 35) test out AR with react web app
- https://github.com/nitin42/React-Web-AR

## 36) mock out turning a github user's contribution data into a sim-city web UI
- each programming language is a type of zone (commercial, industrial, residential...possibly map to compiled vs scripting vs ??? languages)
- height is based on number of merged PRs
- density is based on chronology?
- area is based on number of repos contributed to
- make this into a VR area? like a landscape...commits as height, contributors as area, forks as roads...

## 37) Attempt to redo text highlighting in textarea
- https://github.com/keustma/react-highlighted-textarea
- https://github.com/mcamac/react-text-annotate


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
- investigate whether we can do that following https://24ways.org/2017/feeding-the-audio-graph/
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

## 60) Use vector comparison to find poorly written exam distractors
- maybe BERT would be better for this, not sure
- get data set of exams with questions/distractors
- is it possible to get a data set with item analysis and also data on which
questions students got correct/incorrect?

## 62) Static app visualizer for whether two hosts are on the same network
- similar to netmask-slider, but with only the above question instead of sliding

## 63) Browser based interface to give practice solving recursion problems and/or HOFs
- code sandbox with partially completed recursive functions
- good programmers aren't better at this because they're smarter, just because they've had more practice doing it.
- generate 100 or so similar recursion problems (or possibly a new one every hour?) and have users solve it via coding in the UI
- user sees one incomplete higher order function
- user needs to complete the function
- user presses button
- system runs a test against the output of the function for a given input
- if the output is correct for the test input, then user got it right
- for implementation, see about running JS testing libraries in the browser:
https://medium.com/dailyjs/running-mocha-tests-as-native-es6-modules-in-a-browser-882373f2ecb0
https://stackoverflow.com/questions/33080182/how-do-i-get-node-js-mocha-to-run-test-in-browser
https://stackoverflow.com/questions/42857778/how-do-you-run-mocha-tests-in-the-browser

## 64) Put the n-gram tracing approach to authorship attribution in a docker container
- possibly put it somewhere behind a web interface where we can fire texts at it?
- use python

## 65) Create a native app to record speech and stretch the octave range
- English usually involves between 2-2.5 octaves in normal conversational speech
- Some cultures don't use very wide octave ranges (whether out of politeness or habit)
- The lack of range can suggest things to English listeners (boredom/disinterest/etc), so should not be unconsciously repeated from 1st culture out of habit.

## 66) Remake the python conversational bot treasure hunt via web interface
- Needs a log in, or no way to remember where the user "left off"
(this coule be done with firebase, like in Reactive-Resume)
- should be enough to keep the same script and put users into a simple data schema
- possibly consider using serverless functions for auth

## 67) App and/or website with peer-reviews simplifications of scientific concepts
- Summaries that are gold standard

## 68) Cards Against How Might We - web app version
- put https://github.com/BethFox/CaHMW online as a webapp

## 69) Test out training Text to Speech Model
- play around with https://github.com/r9y9/wavenet_vocoder to see how much data is needed for a passable TTS model
- possibly get single speaker samples from youtube
- identify costs for running something in the cloud for a unique user

## 70) Blog post about using TTS to automate micromaterials in a foundations ESL course
- get audio
- turn it into transcripts
- use transcripts for force-alignment
- get all the AWL (and also possibly new AWL words), as well as the context (entire sentence or window?)
- get all the relative clauses
- get all the -ed simple past tenses
- get all the -s nouns and -s third person simple present verbs
- include blending in audio materials

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

## 75) Collaborate with Julia Evans (B@rk) on using the e-zines to fuel TechEd materials

## 76) Set up static site to track micromaterials on github
- possibly gatsby (needs a search though...)
https://www.gatsbyjs.org/packages/gatsby-plugin-local-search/
https://www.gatsbyjs.org/docs/adding-search-with-js-search/
- filter for bad words


## 77) map out different tech skill areas to target with TechEd
- networking
- security
(outline the main learning objectives in hackone syllabus)
(also include https://sec.eff.org/ )
- a11y
- functions
- design
- vocab
- documentation(?)


## 78) Investigate ways to automate testing with a screenreader
- could we use Speech to Text models to analyze...something...?
- make sure it doesn't read the whole thing at once

## 80) Micromaterial for linux CLI commands
- grep, sed, cat, | , tee, split, ls, wc, rm, mv, cp, pwd, mkdir, tar, find, awk,
sort, uniq, tail, ps, df, du, chmod, chown, ifconfig, uname, less, env, netstat,
dig, head, shuf, tree, cut, lsof


## 83) Plan out a teched site
- include git micromaterials
- include ipinder

## 84) Investigate ways to build out a "methodology" of TechEd
- following : Lee, J. S. (2019). Quantity and diversity of informal digital learning of English. Language
Learning & Technology, 23(1), 114–126. https://doi.org/10125/44675
- ...basically, find out if quantity affects enjoyment/engagement in the same way, and whether diversity of materials affects quantitative outcomes (performance)
- also investigate how to frame Form-Focused and Meaning-Focused in the context of software (syntax/linting vs asserts that a function does what it is supposed to)

## 85) Get a python REPL working in the browser
- https://hacks.mozilla.org/2019/04/pyodide-bringing-the-scientific-python-stack-to-the-browser/
- could be easier to just follow some of the online codesandbox tutorials
- the idea is to also write some tests that verify when learns have "correctly" written the function or completed the function
- similar to #63

## 86) Simple web UI to drag a value and perform integer overflows
- signed 32-bit integers can only go so high until they become negative
- drag values and watch the output "wrap around"
- possibly use a clock as a visual example (subtract 1 minute from 1PM and get 12:59PM...a bigger number)

## 87) Corpus of JS (map, reduce, filter)
- get authentic examples of these three functions (possibly others?)
- present in a web UI (use the coding sandbox format/scaffold)
- strip out bits and have the users put them back in...or something

## 88) Corpus of data structures (maps, arrays, b-trees...)
- how would we recognize these in scrapes of source code?
- how would we then generate them from rules?

## 89) Corpus of function types/signatures
- how would we recognize these from source code? Are there differences between different languages (probably, but need to quantify)
- how would we generate these (language-specific)

## 90) Make simple microservice to show how to calculate resource reservation
- https://medium.com/@vlad.fedosov/how-to-calculate-resources-reservation-for-ecs-task-3c68a1e12725
- (X / 100) * Y * 1.3)
where:
* X — current CPU utilization (percentage)
* Y — value you specified in Task parameters
* 1.3 — buffer capacity you want to reserve for workload spikes (Note: 1.3 value may not fit everyone’s needs, it’s just a baseline)
- knowreservations.netlify.com

## 91) Add quadratic and linear regression to graphit
- quadratic is just ploting the start/end/highest-lowest point
- linear regression is create points on a scatter plot and see how it changes the line
(possibly do something similar for logistic regression, but that might be way too complex)

## 92) fix stress-game on larger screens

## 94) Create micromaterial for practicing CI stuff
- possibly use Henry's approach to accessing github and committing
- github actions fire on commit
- the UI shows the result of the CI build
- one repo has things broken...each branch (possibly by number) has a more complex problem to find and fix
- first three problems (failing test, wrong action name, secret not available in ENV, artifact not available for subsequent step)

## 95) Create corpus of aws docs
- scrape all https://docs.aws.amazon.com
- get list of all links
- get text from all links (can scrapy do this? probably...but bs4 can for sure)

## 96) create simple UI visualization for creating subnets in a network
- how big is the network
- how many subnets can we have? what size can they be
- have CIDR ranges for all of them

## 97) create micromaterial to generate and test the top ten OWASP vulnerabilities
- possibly run a scanner across 10 github repos at a time
- pull out vulnerabilities, and add then to a "vulnerability corpus"?
- cluster by type of vulnerability
- could even have the system fix them slowly, then use that to create a video?

## 98) put pandoc into a docker container to get the JS links on blogs to render
- conceptually very simple, but just need to have a way to actually render the JS
- so we probably need to do it inside chromium (with puppeteer?)
- then grab the rendered html and pass it to pandoc to save into a pocket account
- possibly try the start-server-and-test format, to wait for the HTML to actually
be rendered inside of a simple webserver, then just access the page via curl or something
- currently (kind of) working command to clone entire site:
wget -mk --convert-links --adjust-extension --page-requisites --no-parent -r --follow-tags=iframe -w 3 -e robots=off URL_GOES_HERE

## 99) Make a simple web page to take a phrase/sentence and exaggerate the pitch contours

- follow the approach in https://24ways.org/2017/feeding-the-audio-graph/
- show the visualization both before and after the "stretching"
- possibly model after https://github.com/evykassirer/pink-trombone-bangbangcon
- also check out https://github.com/zakaton/Pink-Trombone

## 100) create react-native app mockups for both Kitchen Rescue and Dog Whistler
- get a version building and deployed to app store

## 101) create micromaterial to practice DNS record stuff
- understanding (select a particular record type from context)
- application (write out the record type and value from context)
- A/MX/AAAA/CNAME/ALIAS

## 102) create mobile app to connect images to core-meanings
- based on the EFL Notes blog post "Funky Images"
- one central character that does stuff based on how you swipe
- possibly incorporate a text element...show word in sentence and change it based on where the gesture moves to (left makes it past tense, right makes it future, circles in the middle makes it continuous, circles on the left makes it past continuous...)

## 104) create simple micromaterial for using dev-tools lighthouse audit
- put it in a webapp that opens chrome dev tools automatically
- bake in one thing per audit category that needs fixing
- walk people through fixing stuff, with one fix/category per git tag
- users can check out the specific tags to see the fixes (or just git log them)

## 106) inline/block html micromaterial
- base this off b0rk's simple graphic


## 108) mobile app to teach nonverbal floor bid cues
- the fish
- possibly hand gestures
- automated script on repeat...stops and yields the floor

## 109) Stresseoke
- take lyrics from genius.com and display them below an embedded component showing a youtube video
- possible to sync lyrics with spoken words (via color/size/etc?)
- what's the best way to compute expected stress pattern (90% is probably good enough)
- how to show stress in words (resizing/animation/bolding?)

## 111) draft micromaterials for economics concepts
- affects of inflation on asset prices/bond prices/debt/etc
- basically, I don't understand any of this stuff, so would be nice to have a very basic material to gives feedback on ability to apply these concepts
- eg, UI shows current futures pricing for a particular asset and also forecasted inflation, then user selects whether futures price will go up or down
- (hard level, user selects rough estimate for how much the price will go up or down)


## 114) micromaterial to show/calculate highest number of connections for an RDS database on AWS
- DBInstanceClassMemory/12582880...so for t2.micro with 512MB RAM, (512 * 1024 * 1024) / 12582880 => 40-ish

## 115) create some sort of difficulty ranking for https://github.com/danistefanovic/build-your-own-x
- one single metric probably won't work for every project (different languages, tools to measure things, etc)
- something universal could be a good first step (eg, lines of code)
- mock up a simple WebUI where you can explore simple metrics about these, and just pull the source from this repo...probably clone and preprocess as a separate repo
- sub-topic...would it be helpful to create a project that just outputs lines of code in a given repo? This may or may not already exist, and github probably already has it somewhere. Ditto with number or files.
- other possible metrics: number of functions, average function size, average distance from variable to invocation (no idea if this is even feasible, but would be cool)

## 116) Publicly praise places that are using good code review comment structure

look at these for templates:
- https://conventionalcomments.org/
- https://www.netlify.com/blog/2020/03/05/feedback-ladders-how-we-encode-code-reviews-at-netlify/

- write a github scraper that looks at the big orgs (where to get a list of these?) and scrapes all the PR's from each project
- very simple MVP at to whether the comments show any systemic structure (maybe via pulling out the similarities at a very high level)
- then use this data to create a web app to show the companies that are doing this a bunch (look at the two resources above and target those companies first, as baselines)
- use https://github.com/typescript-cheatsheets/react-typescript-cheatsheet/
(basically `npx create-react-app --template typescript`)

## 117) Make this into a webapp
- https://github.com/cardsagainstcontainers
- maybe also use typescript

## 118) Somehow contribute to a catalog of resources for Tech Ed (but ed in general)
- https://hackeducation.com/
- reusability paradox describes codeacademy/freecodecamp/etc very well...the usefulness is inversely corelated to its reusability. Stated another way, the more actually focused something is, the less it can be used in a decontextualized way (which is obvious, in one sense)
- https://opencontent.org/blog/archives/3854
(posits that the way to escape this paradox is to make something open-source, and therefore inherently reusable/remixable)

# 119) Functions but with cloze completions
- if we can parse lots of languages with JS in the browser, we should be able to remove 1-2 lines from a function and ask the user to supply what they "should" be
- we can then provide feedback on whether the function actually "runs"
- we can also provide feedback on whether the re-written function "does the same thing" (this is related to the functionality of #63)

# 120) Comprehension-based material to match problems and formal constructs
- "The semantics of a for statement (a program component) are mixed up with what the for statement is used for in the particular context. Vainio and Sajaniemi [2007] describe such violations of robustness principles as common, attributing this in part to the tendency in CS1 courses to associate each type of problem with only a single kind of programming construct, and each programming construct with a single kind of problem."

# 121) A VR (AR?) game to visualize and play with objects/classes/OO stuff
- classes would possibly be 2D squares that could be filled with data and other properties and converted to 3D cubes.
- the user can move them around and see the connections between them.
- the user can also run a particular program forward or backward and watch the system (in terms of physical "objects") interact
- this system could be designed to take in any arbitrary program to be visualized


# 123) Micromaterial to practice creating an allow list via regex for web form validation
- ideally with a bunch of inputs listed and asking for a regex that would allow through only the ones we know we want
- possibly more rather than less hand-holding, though also make this configurable

# 124) Micromaterials to practice using ssh command line utility and step through common use cases and troubleshooting
- maybe wrap it in a go binary to enable custom sending of feedback
- ...also maybe look at creating a WASM binary from ssh and doing something in a web UI

# 125) Create micromaterial for discovering and setting/updating permissions
- windows & mac & linux

# 126) Look at corpus of hackyourfuture.be written language
- go to the site and apply (add note about just looking)

# 127) Micromaterial where learners identify the line number where the mistake is
- there's a bug
- there's an error message
- there's a function
- users need to click/identify/choose which line has the error

# 128) Micromaterial to show app/load balancer latencies and how it affects autoscaling groups
- When EC2 instances have processes that can't respond fast enough, requests start backing up.
- When these requests stop being all responded to, some of them are probably helath checks
- When enough health checks fail, the ELB will take the EC2 out of service
- When one of the EC2 instances gets killed, the rest experience higher load, and then all fail.
- show this is a web app where users can adjust latency of response, period for health check, and requests per second

# 129) Create a corpus of content on the MDN docs
- also check the glossary to see if those terms could be better

# 130) Use Ben's lidar thing to visualize tcp traffic going between containers
- containers since you can have fine-grained control over tcpstuff without needing anyone to install anything except docker
- needs lots of exploratory data analysis, since I'm not even sure what things are going to be interesting
- possibly look at the tcp traffic involved in a basic rails app (frontend/backend/database), and be able to filter for stuff(?) in the browser

# 130) Use tensorflow JS to make a Simon Says for simple English practice
- calculate where people's hands are and give simple commands (either written or audio) like "move your left hand up", "move your right hand down", or "keep both hands up".
- give automated feedback about whether they did it correctly.
- we don't have any depth information, just 2D, so have to stay with up/down/left/right.
- Possibly create a game interface, where two people "compete" for longest streak, and take turns holding the phone.

# 131) Automate a "break a system and then fix it" activity

- probably easiest to do with a homelab in a very predictable configuration (4-5 VMs with private IPs)
- Get some ansible playbooks (or some other IAC tool) that can spin up a very simple service architecture: Database, backend server, cache, SIMPLE frontend web server
- set up montoring dashboards and logging (grafana and ELK stuff)
- plan out 3 "fail scenarios", and fire one randomly

# 132) Figure out a way to add in authentic examples to https://codethesaur.us
- probably needs to involve the datastore
- maaaaaaybe could be grabbed in a github action and hardcoded?
- a very far way off from this, but a similar-minded project that could benefit from authentic examples from real code

# 133) Turn pulse game concept into an app (or something)
- incorporate the 120 scenarios from Hooper's old Pulse concept
- would probably have to be a mobile app
- paired with a bluetooth device that can sense heartrate

# 135) Visualize crashing a DB with connections
- when services scale up, if they're expecting to create a connection to a database, a massive scale up means a flood of new connections.
- If too many processes try to open too many connections, it kills the DB...but it would be nice to see how (in dashboards/logs)
- possibly use a docker MongoDB replicaset for this, though how to spin up 50+ containers locally might be trickier.


# 137) Kubernetes the hard way on Sigmacloud
- this is going to be *very* bootstrapped, since they have no VPC, no load balancers, and no CLI...just a REST API.
- probably gonna try and make a golang cli to actually complete this one

# 139) Get a pitch together for a P1PP micromaterial course/material/something
- "chaos engineering without the chaos" (get a way better slogan)
- predictably break a system and get automated feedback about whether you fixed it
- needs alerts
- needs dashboards
- needs logs
- needs a "system" to perturb
- needs metadata about what actions were taken and when
- "controlled chaos"
- https://education.ardanlabs.com/

# 140) Create a twitch stream for the "Chaotic Good" project
- think of a better name
- invite notable SRE personalities and have them fix a simulated outage
- Get some *basic* AWS environments built out in terraform, ready to deploy before the stream
- Create 3-5 different scenarios for outages, and create the alerts for these (we can put it all in source transparently, but we need a _secret_ way to select which one gets triggered...probably via me kicking off _something_ on my side)
- Figure out how to auth in the guests (plus also create SSH keys to be sent to them beforehand) via IAM roles
- figure out the best platform to send alerts to (some people might prefer slack or discord or?)
- Figure out how to reliably stream the action (it probably can't be their screen, since that doesn't scale if they don't stream).
- Do we include a post-mortem (hopefully yes, but probably based on time constraints)
- Do we include any "phone a friend" capability?

# 141) Slide Deck for Chaotic Good project
- Show need for faster iterations of learning from production outages in "safe" environment
- It's an activity to contextualize what Google already does with Wheel of Misfortune
- Need good examples to make it relatable

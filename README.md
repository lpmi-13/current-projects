# current projects

```
# copyright Pete Langley 2018
#
# don't have more than three things on the go at once
```
## 160) Code Corpus API
- we've got data sorted with https://github.com/lpmi-13/code-corpus-collector
- we need a list of things people would want to use this for
- for now, we can do without update of the data...just cause there's already enough to keep us going for a while
- we probably need a landing page at the main domain (codecorpus.net), and then have the api respond at the subdomain `api.codecorpus.net`.

## 148) set up a simple AWS environment with a three-tiered architecture and then break it
- related to #140
- https://jaxenter.com/chaos-engineering-cpu-spike-174107.html
- get a list of other things to cause problems
- figure out a good base domain to have for my examples (do-some-chaotic-good.com)?
- figure out a good base domain to have for my examples (do-some-chaotic-good.com...?)...AWS can register .com domains, so just pick one and use that as the base piped into the terraform code
- use some ideas from https://www.thevoid.community/ open incident database
- for the failure scenarios include: 1 - A can't talk to B (networking issue, DNS, firewall, service not up etc etc)...2 - server degraded (high CPU, high IO, OOMs etc), this may come from runaway process or faulty code (say N+1 ORM issue)...3 - configuration issues (nginx or whatever with bad config, bad SSL cert etc) ...1 and 2 can be approached systematically and 3 depends on extra knowledge of particular tooling etc

## 186) Micromaterial to practice back-of-the-envelope calculations
- How many characters does your GUID need? Eg, for a given number of users, a given number of items in a database, a given number of X to keep track of...
- Capacity estimates and constraints
- traffic estimates (breakdown between read/write in difficult mode, just total traffic/requests in easy mode)
- queries per second (per minute?)
- storage estimates (number of "things" to storage, and total storage space needed)...maybe also consider if we want to keep data for X years
- bandwidth estimates (how many requests per second * size of request)
- memory estimates (in case of caching)
- how much percentage of the requests should we cache (figure out number of requests and then how many of those requests we expect to hit the cache)

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
- add ability to filter by "complexity" if possible
- get input from the #accessibility channel about how best to make this usable via screen readers
- investigate using JS-based AST parsers in the browser to evaluate the "correctness" of the re-order instead of just the literal order (maybe tree-sitter?)
- investigate only storing the beginning/ending of the function lines from the github source code and using github as an open API to grab this stuff at runtime (disadvantage would be that code changes, though this is also technically an issue if we are storing pointers to line numbers anyway)
- see if there's a way to turn loops (maybe this should be in a different micromaterial) into blocks, as evan suggested.

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
- maybe gitpod is a better platform for this?

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
- good programmers aren't better at this because they're smarter, just because they've had more practice doing it.
- generate 100 or so similar recursion problems (or possibly a new one every hour?) and have users solve it via coding in the UI
- the original idea is done with the https://github.com/lpmi-13/higher-order-functions
- now the difficult part is actually generating recursive functions

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
- working title: Solodex
- Facebook, but no data leaves
- A place to write notes in a well-designed format about family/friends
- Set reminders for yourself to send Xmas cards, birthday cards, etc
- Instead of people adding you, only you add people
- Kind of like a digital rolodex

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
- https://dev.to/craigmorten/a11y-testing-automating-screenreaders-1a3n

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

## 119) Functions but with cloze completions
- if we can parse lots of languages with JS in the browser, we should be able to remove 1-2 lines from a function and ask the user to supply what they "should" be
- we can then provide feedback on whether the function actually "runs"
- we can also provide feedback on whether the re-written function "does the same thing" (this is related to the functionality of #63)

## 120) Comprehension-based material to match problems and formal constructs
- "The semantics of a for statement (a program component) are mixed up with what the for statement is used for in the particular context. Vainio and Sajaniemi [2007] describe such violations of robustness principles as common, attributing this in part to the tendency in CS1 courses to associate each type of problem with only a single kind of programming construct, and each programming construct with a single kind of problem."

## 121) A VR (AR?) game to visualize and play with objects/classes/OO stuff
- classes would possibly be 2D squares that could be filled with data and other properties and converted to 3D cubes.
- the user can move them around and see the connections between them.
- the user can also run a particular program forward or backward and watch the system (in terms of physical "objects") interact
- this system could be designed to take in any arbitrary program to be visualized


## 122) Micromaterial to visualize placing ECS tasks into instances in a cluster
- make sure the task reservations (CPU/RAM) are variable and also that the VM specs are variable
- probably just drag and drop "taks" into VMs to watch how mismatches might throw specific errors: unable to place task because no container instances met all of its requirements
- see if anyone on awsnewbies or cloudnewbies finds this useful

## 123) Micromaterial to practice creating an allow list via regex for web form validation
- ideally with a bunch of inputs listed and asking for a regex that would allow through only the ones we know we want
- possibly more rather than less hand-holding, though also make this configurable

## 124) Micromaterials to practice using ssh command line utility and step through common use cases and troubleshooting
- maybe wrap it in a go binary to enable custom sending of feedback
- ...also maybe look at creating a WASM binary from ssh and doing something in a web UI

## 125) Create micromaterial for discovering and setting/updating permissions
- windows & mac & linux

## 126) Look at corpus of hackyourfuture.be written language
- go to the site and apply (add note about just looking)

## 127) Micromaterial where learners identify the line number where the mistake is
- there's a bug
- there's an error message
- there's a function
- users need to click/identify/choose which line has the error
- use dumb init for this https://github.com/Yelp/dumb-init
- copy an application into a container and delete random parts of it, then pipe the stdout/stderr to a file...do this 100,000 times (more maybe?)

## 128) Micromaterial to show app/load balancer latencies and how it affects autoscaling groups
- When EC2 instances have processes that can't respond fast enough, requests start backing up.
- When these requests stop being all responded to, some of them are probably helath checks
- When enough health checks fail, the ELB will take the EC2 out of service
- When one of the EC2 instances gets killed, the rest experience higher load, and then all fail.
- show this is a web app where users can adjust latency of response, period for health check, and requests per second

## 129) Create a corpus of content on various docs sites
- MDN docs
- AWS docs
- GCP docs

## 130) Use Ben's lidar thing to visualize tcp traffic going between containers
- containers since you can have fine-grained control over tcpstuff without needing anyone to install anything except docker
- needs lots of exploratory data analysis, since I'm not even sure what things are going to be interesting
- possibly look at the tcp traffic involved in a basic rails app (frontend/backend/database), and be able to filter for stuff(?) in the browser

## 130) Use tensorflow JS to make a Simon Says for simple English practice
- calculate where people's hands are and give simple commands (either written or audio) like "move your left hand up", "move your right hand down", or "keep both hands up".
- give automated feedback about whether they did it correctly.
- we don't have any depth information, just 2D, so have to stay with up/down/left/right.
- Possibly create a game interface, where two people "compete" for longest streak, and take turns holding the phone.

## 131) Automate a "break a system and then fix it" activity

- probably easiest to do with a homelab in a very predictable configuration (4-5 VMs with private IPs)
- Get some ansible playbooks (or some other IAC tool) that can spin up a very simple service architecture: Database, backend server, cache, SIMPLE frontend web server
- set up montoring dashboards and logging (grafana and ELK stuff)
- plan out 3 "fail scenarios", and fire one randomly

## 132) Figure out a way to add in authentic examples to https://codethesaur.us
- probably needs to involve the datastore
- maaaaaaybe could be grabbed in a github action and hardcoded?
- a very far way off from this, but a similar-minded project that could benefit from authentic examples from real code

## 133) Turn pulse game concept into an app (or something)
- incorporate the 120 scenarios from Hooper's old Pulse concept
- would probably have to be a mobile app
- paired with a bluetooth device that can sense heartrate

## 135) Visualize crashing a DB with connections
- when services scale up, if they're expecting to create a connection to a database, a massive scale up means a flood of new connections.
- If too many processes try to open too many connections, it kills the DB...but it would be nice to see how (in dashboards/logs)
- possibly use a docker MongoDB replicaset for this, though how to spin up 50+ containers locally might be trickier.

## 139) Get a pitch together for a P1PP micromaterial course/material/something
- "chaos engineering without the chaos" (get a way better slogan)
- predictably break a system and get automated feedback about whether you fixed it
- needs alerts
- needs dashboards
- needs logs
- needs a "system" to perturb
- needs metadata about what actions were taken and when
- "controlled chaos"
- https://education.ardanlabs.com/

## 140) Create a twitch stream for the "Chaotic Good" project
- think of a better name
- invite notable SRE personalities and have them fix a simulated outage
- Get some *basic* AWS environments built out in terraform, ready to deploy before the stream
- Create 3-5 different scenarios for outages, and create the alerts for these (we can put it all in source transparently, but we need a _secret_ way to select which one gets triggered...probably via me kicking off _something_ on my side)
- Figure out how to auth in the guests (plus also create SSH keys to be sent to them beforehand) via IAM roles
- figure out the best platform to send alerts to (some people might prefer slack or discord or?)
- Figure out how to reliably stream the action (it probably can't be their screen, since that doesn't scale if they don't stream).
- Do we include a post-mortem (hopefully yes, but probably based on time constraints)
- Do we include any "phone a friend" capability?

## 141) Slide Deck for Chaotic Good project
- Show need for faster iterations of learning from production outages in "safe" environment
- It's an activity to contextualize what Google already does with Wheel of Misfortune
- Need good examples to make it relatable

## 142) Find some gaps in scaleway cli and submit a PR
- Easiest way to do this would be to start working on the k8s-the-hard-way walkthrough with it and see where the gaps are

## 143) K8s the hard way on scaleway
- Possible that the CLI, which is very new, needs some functionality added to be able to complete the walkthrough


## 145) Homelab network expansion
- get one pi for just prometheus/grafana
- fire up three VMs on the mini (also decide what to put in three VMs)
- step though https://grafana.com/blog/2019/08/22/homelab-security-with-ossec-loki-prometheus-and-grafana-on-a-raspberry-pi/

## 146) K8s the hard way on OVH
- they have a defunct CLI and not really great API docs, so this one might require a bit of upfront work to actually even get a command line client working

## 147) Match up songs for lyrics plus karaoke tune
- grab beats per minute (tempo) from spotify API for a number of different artists
- https://www.uswitch.com/broadband/every-countrys-favourite-karaoke-song-mapped/
- https://github.com/benjojo/bpm
- also look at using metadata from the spotify audio features API
- output pairs of songs from different genres that have similar factors (x, 2x, 1/2x, etc) and sing karaoke with the melody of one and the lyrics of another


## 149) Create a micromaterial to match function type signatures in typescript with plain JS objects
- Utility types matched with what happens when you use them
- return signatures matched with which Object is an example of that
- other very basic, but easy to forget stuff

## 150) Create a learning space focused on InfoSec stuff
- hackxper.com/JWT (and others)
- tryhackme.com

## 151) Create micromaterial based on CS Unplugged binary search activity
- start at the root node and the graphic leads you down towards each branch
- before you get to a branch, you have to swipe left or right to navigate to the correct place
- a kinesthetic algorithm
- similar to guitar hero, but way more basic (read: achievable)

## 152) Put broke robots phrases on postcards

## 153) Investigate using opentelemtry for micromaterials
- See what can be sent from a webapp
- See what the easiest method to collect this data might be (cost/effort/etc)
- See if that data can be easily displayed somewhere

## 154) Create a micromaterial to convert code to a notional machine
- investigate more the ways that a notional machine might be visualized
- Could be a VR/AR representation of a control structure (or something)
- Highlight that the variable/function definitions can (sometimes) be moved around without changing the execution of the program

## 155) Create micromaterial (maybe in gitpod) to use strace to confirm why a container can't startup
- possibly trying to bind to a privileged port (eg, 80) without running as root...but that would probably be very obvious from the error message

## 156) See if any of the NACE workshop stuff can be turned into a micromaterial
- https://www.cerias.purdue.edu/site/nace/

## 157) Work through justjavascript.com and see the relevance for micromaterials
- https://justjavascript.com/

## 158) Create Cloud Compose DAG Dojo micromaterial
- set up with terraform (this is going to take a long time to work out, since apparently it takes about an hour to provision, and config errors aren't detected until you actually try to run it)
- Three failure modes: network, permissions, instance size/type issues
- possibly add in alerts to a slack channel (script it)

## 159) Create a mockup for CSS wordle (CSSdle?) micromaterial
- see if CSS things can be put into categories (to enable automated feedback)
- see about creating UI for just two states (before/after)
- see about selecting 3 transformations to apply to create the "after"
- see about grading the "CSS categories" by difficulty (eg, color is "easy", and transforms are "difficult).

## 160) Use the shift-fuzzer-js for creating random function declarations
- figure out something to do with this
- https://shift-ast.org/fuzzer.html

## 161) See how much this (or things like this) could be made into a gitpod-based workshop
- https://gist.github.com/jedrichards/9942165

## 162) Create learning space for Rana Khalil's security stuff
- https://ranakhalil.teachable.com/p/web-security-academy-video-series
- other stuff she does

## 163) Create learning space for the 90 days of devops github repo
- https://github.com/MichaelCade/90DaysOfDevOps

## 164) Create corpus of transcript/audio for Darknet Diaries
- How to talk like an infosec person
- Will need lots of exploratory data analysis to see what falls out
- https://www.youtube.com/watch?v=RrH4qOYt6P0&list=PLtN43kak3fFEEDNo0ks9QVKYfQpT2yUEo

## 165) Create a single serving webpage that provides "people shout at you during your live coding tech test" as a service
- two people on the call
- maybe a third one joins midway?
- recorded separately with colorful costumes
- spliced together and served via a single webpage

## 166) Use gitpod to create cloze tests for...things
- don't recall what this idea was about, but an interesting concept

## 167) Micromaterial for & and * in Golang
- I keep forgetting which means which, and for people coming from languages without much use of explicit pointers (JS/python/ruby), this is going to be totally new, so just something to practice reading/writing them
- which things means a memory address, and which things means the value at that address
- you have a memory address...which thing is going to refer to that (and same for the value of a pointer)

## 168) Micromaterial to practice using tc
- traffic control...simulate dropped packets and corrupted packets and all kinds of network issues.

## 169) Micromaterial using tcpdump101.com
- also V2 at dev.tcpdump101.com

## 170) Micromaterial to practice parsing logs via the commandline
- Mix terminal and web UI via gitpod
- Take initial dataset and ask things like "how many times does X" occur, then have them press a button in the Web UI
- Ideally, the question/answer pairs can be at least a bit random, so that it's not the same activity every time, but probably MVP will be just using a subset of hardcoded Q/A pairs for each "run" of the activity
- eg, "how many times does this npm command use the bind() syscall?"
- eg, with large dataset, "how many unique users are in these logs?"

## 171) Make a codewords implemenation
- based on https://github.com/jaredreisinger/react-crossword
- then take away clues
- then get a dataset for the words
- then decide on how to organize the dataset for each letter occurring how many times (or whatever codewords uses)

## 172) List of all public GitHub repositories
- available at https://docs.github.com/en/rest/repos/repos#list-public-repositories
- with an auth'ed user, we can get 5,000 requests per hour (with 100 results per request), which means it'll be about 41 days to grab everything.
- store the repo ID, since that's what we paginate by, and it also means we can just query the diff later.
- put this in a container and probably run it on the mac mini (since I'm doing literally nothing with it).
- storing just the URL and the ID should be around 300MB for all 492 Million repos (based on testing in the browser).

## 173) Create a docker container for computing item analysis
- start with https://github.com/patriciamar/ShinyItemAnalysis
- semi-working prototype at https://github.com/lpmi-13/item-analysis

## 174) Use gdb (probably in a gitpod) to analyze core dumps
- start with https://www.brendangregg.com/blog/2016-08-09/gdb-example-ncurses.html
- see if you can find a corpus of core dump data

## 175) Add recursion detection to corpus collection
- https://docs.python.org/3/library/inspect.html#inspect.getclosurevars to find all the recursive functions (maybe there's also a simpler way)

## 176) Figure out a micromaterial for the We Hack Purple stuff
- https://wehackpurple.com/pushing-left-like-a-boss%E2%80%8A-%E2%80%8Apart-5-10%E2%80%8A-%E2%80%8Auntrusted-data/

## 177) Micromaterial for just checking whether a site is vulnerable to CSRF
- JWT in auth header, not vulnerable
- passed in cookie, could be vulnerable
- a relevant action (maybe ask for clarification on this)
- no unpredictable request parameters (maybe this just means not ignoring unexpected params)

## 178) Micromaterial for fixing relative imports in python
- just set up a simple app in gitpod that doesn't work because the imports are bad
- then fix them
- also do this for golang (separate repo)

## 179) Micromaterial to set and grep for correlation ID
- set random UUID's in the HTTP request headers, and track a transaction across different services
- set something like X-Correlation-Id
- possibly start out with a problem in some 3-service (or whatever number) architecture, and then add in the correlation ID and check logging in Kibana to see where the problem is

## 180) See about converting common leetcode questions to things that are more "social" (ie, involving people)
- https://en.wikipedia.org/wiki/Wason_selection_task#Explanations_of_performance_on_the_task
- Cosmides and Tooby (1992) and found instead that "performance on non-arbitrary, evolutionarily familiar problems is more strongly related to general intelligence than performance on arbitrary, evolutionarily novel problems"

## 181) Micromaterial to supply the missing part of recursive functions
- this is going to be HEAVILY focused on the tests
- basically have the tests completely specify the scenario (how many "things" are adjacent)
- the recursive functions could be partially complete, or even just have the function name defined, with nothing else
- put it in gitpod, naturally
- do it in typescript and/or python

## 182) Web app to let groups of learners submit summaries for a method/function in an open source repo
- needs a login, so we can group people by class/cohort/etc.
- this way, we probably don't need to worry about content moderation
- group owner (the person who sets up the group) can send invites and allow people to join, or also make other members owners
- users submit summaries (short) of functions, and they can also read the summaries that other users in the same group have written.
- natural activity to complement a learning space for a small cohort of learners

## 183) Micromaterial to present faded code blocks
- possibly fade out the keywords, or some other aspect of a working program.
- the benefit of putting this in a runtime environment is you can probably even add tests, and when you've "unfaded" the code, the tests pass
- we also get feedback from whether it runs/errors.

## 184) Trainline PR choose your own adventure
- Get an org with a starter template that can be used to create a new repo and assigned to a particular github user (both Wilco and CYF do this).
- One backend (stateless and in typescript), behind nginx, one data store (probably postgres run locally in a container), one frontend (react w/ typescript), and one lambda (python?) to put the data in the database periodically
- In that repo, assign a first PR that just adds a single method to respond to a particular path in the backend. Solicit all feedback, comments, etc
- after initial PR merge (this is probably the only step without branching), trigger an automated issue from the tech lead to increase code coverage above 75% (or whatever).
- slightly after (maybe 5 min or so), raise another PR to add some different handling, maybe update the model in the backend. This could have bugs in it.
- if the above code gets merged (with or without the bugs), have the tech lead raise an issue that the frontend is now broken and needs to be updated to handle the new data model and response from the backend.
- for whatever code the user merges in (could be in a PR, but maybe simple to push a hotfix to main), run the CI and see if the tests pass.
- the CI needs to be in GitHub actions, and will run unit tests on PRs, but also ideally run integration tests using cypress at a particular branch (either on gitpod or netlify).
- we also need to update the python script that feeds the database, but maybe that's out of scope for the initial MVP of this. Ideally it would need to be updated to feed in (or just not filter out) the data that matches the data model of the backend when it changes.
- The automated CI of this is key...depends how easy it is to deterministically run an integration test in either gitpod or netlify. For gitpod, we can probably just have the user do something manual, and actually, maybe netlify isn't really an option, since we need a backend for anything integration-esqu


## 185) Create a CLI client for cloudsigma
- has a REST API, so we need one go library to manage interaction (gocs), and one CLI to use that library (sigmactl). Since I'm still learning go, these are going to be heavily influenced by the digital ocean golang CLI.


## 187) Chaos-pod
- controlled chaos in a gitpod
- we need the smallest possible bunch of stuff that we can deterministically break (network partition, load, and maybe bad config updates)
- use github.com/wg/wrk to generate load
- use tc to simulate network partitions
- simulate new deployments of config maybe
- possible issue that we can abstract away the actual configuration of the issues via a web UI (so that "setting" security group rules "looks" the same in our pod as it does in an authentic situation), but then the interrogation of what the actual issue is could get a bit muddled, and the implemenation will be WAY heavier...

## 188) AR for cubetto thing
- just make something with AR Kit for react native
- if possible (and it actually works and stuff), see about joining the iOS dev program, just to get experience with that whole fiasco

## 189) ShouldIPartitionIt (maybe .com)
- a webapp (map, not territory) to examine what happens if you have a given data schema and decide to partition on different parts of it
- intent is to _show_ how parititioning on things with higer variation (eg, users' location) is "better" than paritioning on things with lower variation (eg, users' gender).
- could we include the idea/visualization of a "hot" partition?

## 190) MySQL Dojo
- a simple micromaterial (similar to the mongo dojo) to practice common tasks in a MySQL database.
- could be that we really just care about is just seeing different failure modes for this database, so maybe we just set up a containerized database with prometheus and grafana to monitor, then create different ways to load it to failure
- one fun way to do this would be the web UI + k3s cluster + BOOM

## 191) Elastic Dojo
- simple micromaterial to see how/when Elastic search fails
- could be that without sufficient scale, it's not possible to learn anything meaningful, but I also have never done anything with ES management, so anything here would result in learning stuff I don't know now.

## 192) Overload Scenario
- originally conceived of as just mimicking Black Friday, but it could be that this is very similar to the dojos anyway.
- maybe the best learning would just be researching and documenting the different ways to create load, and also looking at the tradeoffs of low per transaction data througput but high transaction volume VS high data payloads per transaction with slightly lower transaction volumes.
- the whole point would be to tease out what a bunch of terms (eg, "iops", "throughput", "saturation") mean in practice, and experiment with how we would create different conditions affecting those things.

## 193) Debugging Checklist
- basically, I keep forgetting simple things while debugging (like checking thequotes), so I need a checklist to remind me of the super simple stuff to check
- quotes
- spelling
- white space
- is it on?
- etc

## 194) JQ practice engine
- a web-based (and terminal-paired) way to practice using `jq` to manipulate data
- a server with 3 pairs of endpoints (to start), eg, `question1` and `answer1`, and a web-ui that tells you how to manipulate it and whether you did it right.
- GET request from the first endpoint, and a post with the json data to the second endpoint in the pair.
- when you submit the correct data, the UI changes to show a green tick next to that problem.
- take a json array and return the first element
- take a json map and return the values for a specific key
- take a json array of object and return the total value for all keys of a certain type
- do lots of mapping, reducing, and filtering.
- eventually, would be nice if the problems autogenerate, though I have no idea how that would be accomplished.
- could a compose stack start a container with a certain "seed" in its config for the type of problem? Then, when the post succeeds, it send a SIGTERM and the compose stack knows to spin up a new container?
- if only process-based, the process would have to store the state of the call to the GET endpoint so it knows that subsequent requests don't update anything until the POST succeeds, then the GET endpoint response payload updates along with the POST endpoint.

## 195) How big is that json?
- a web-based micromaterial to help people estimate the size of a json payload by sight
- have one randomly generated json payload (maybe use faker or something simple)
- have three buttons to click to show your guess
- give immediately feedback about whether it was the correct guess
- try to have all three options fairly close together...maybe like half a standard deviation distance from middle to the other ones...

## 196) SLOConf submission
- Make a simple webapp that "does stuff"
- Show the compose stack dashboards in grafana
- Make the Login buggy (maybe every 10th login fails)
- Make the sessions slow (store them in the DB)
- Make the DB requests generally slow (don't use connection pooling)
- Have the query not use an index
- Constrain the memory (for containers with Elasticsearch)
- Show the SLOs in the grafana instance and walk people through fixing the three issues so that the SLO's are no longer breaching
- Fix buggy code
- Move sessions to a caching layer
- Implement connection pooling
- Add an index
- Bump the memory for the ES container

## 197) Get some simple micromaterials (maybe one that branches off?) for Julia Evans Linux Debugging Zine
- awesome tools in here and great examples, so put some of them into exercises

## 198) How to talk like an SRE
- grab audio/transcripts from https://www.oncallmemaybe.com/
- grab audio/transcripts from https://sre.google/prodcast/
- grab audio/transcripts from https://smallbatches.fm/episodes (this one might not be as relevant)
- this one only has transcripts in youtube, but we can grab that and the audio in one place (plus the API might be nicer than webpage scraping) https://www.youtube.com/@SlightReliability

## 199) Feeling what different SLOs are like
- this isn't necessarily about feeling things, but more about conveying the difference between a page load latency of 200ms, 500ms, and 1000ms.
- there are probably other things that we could simulate different tiers of SLI for, like time to interactive and other web vitals stuff
- possible issue is that these client-side metrics are highly dependent on things like device type and network conditions, but at least we can "preview" the actual client experience
- put a random generator on the server side to simulate latency levels, and then you can just swipe left or right based on whether you think the latency was "acceptable"...then click "generate SLO" whenever you're ready to see what it would have been

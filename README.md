# current projects

```
# copyright Pete Langley 2018
#
# don't have more than three things on the go at once
```

## 205) remotehack global view
- would be cool if every last Saturday of the month we have a global map of everywhere doing a remotehack
- use cloudflare workers and Edge sqlite database to set state for which countries are having remotehacks
- either put a link on remotehack.space or some other domain (eg. remotehack.global or something)

## 196) SLOConf submission
- Run this all on a custom playground in labs.iximiuz.com
- Make a simple webapp that "does stuff"
- Show the system dashboards in grafana
- Make the Login buggy (maybe every 10th login fails)
- Make the sessions slow (store them in the DB)
- Make the queries always hit the database (not stored in a caching layer)
- Make the DB requests generally slow (don't use connection pooling)
- Have the query not use an index
- Constrain the memory (for containers with Elasticsearch)
- Show the SLOs in the grafana instance and walk people through fixing the three issues so that the SLO's are no longer breaching
- Fix buggy code
- Move sessions to a caching layer
- Move common query results to a caching layer
- Implement connection pooling
- Add an index
- Bump the memory for the ES container
- (this is a bit of a stretch, but would be nice to show a transition from a pull-based architecture to an event-based push architecture...something like requests from rando devices want to get updates about things but the service they call has upstream dependencies it needs to wait for to aggregate things...transition from those upstream dependencies notifying (via whatever method) the downstream service of changes via some sort of message passing, and then it's able to respond more or less immediately to the calling device)

---

## 148) set up a simple AWS environment with a three-tiered architecture and then break it
- related to #140
- https://jaxenter.com/chaos-engineering-cpu-spike-174107.html
- get a list of other things to cause problems
- figure out a good base domain to have for my examples (do-some-chaotic-good.com)?
- figure out a good base domain to have for my examples (do-some-chaotic-good.com...?)...AWS can register .com domains, so just pick one and use that as the base piped into the terraform code
- use some ideas from https://www.thevoid.community/ open incident database
- for the failure scenarios include: 1 - A can't talk to B (networking issue, DNS, firewall, service not up etc etc)...2 - server degraded (high CPU, high IO, OOMs etc), this may come from runaway process or faulty code (say N+1 ORM issue)...3 - configuration issues (nginx or whatever with bad config, bad SSL cert etc) ...1 and 2 can be approached systematically and 3 depends on extra knowledge of particular tooling etc


## 128) Micromaterial to show app/load balancer latencies and how it affects autoscaling groups
- When EC2 instances have processes that can't respond fast enough, requests start backing up.
- When these requests stop being all responded to, some of them are probably health checks
- When enough health checks fail, the ELB will take the EC2 out of service
- When one of the EC2 instances gets killed, the rest experience higher load, and then all fail.
- show this in a web app where users can adjust latency of response, period for health check, and requests per second

## 131) Automate a "break a system and then fix it" activity

- probably easiest to do with a homelab in a very predictable configuration (4-5 VMs with private IPs)
- Get some ansible playbooks (or some other IAC tool) that can spin up a very simple service architecture: Database, backend server, cache, SIMPLE frontend web server
- set up montoring dashboards and logging (grafana and ELK stuff)
- plan out 3 "fail scenarios", and fire one randomly

## 171) Micromaterial to practice parsing logs via the commandline
- Mix terminal and web UI via gitpod
- Take initial dataset and ask things like "how many times does X" occur, then have them press a button in the Web UI
- Ideally, the question/answer pairs can be at least a bit random, so that it's not the same activity every time, but probably MVP will be just using a subset of hardcoded Q/A pairs for each "run" of the activity
- eg, "how many times does this npm command use the bind() syscall?"
- eg, with large dataset, "how many unique users are in these logs?"
- most common IPs, unique clients, and success rate over the past hour
- possibly combine with awksedfred

## 207) I do, we do, you do
- for a very simple activity (maybe curling an endpoint or something), generate code that doesn't work, and get an automated system (chatGPT maybe?) to fix it.
- PoC MVP might be asking chatGPT to generate some unoptimized code (eg, python summing a list instead of using the native `sum` built-in), which it knows how to fix.
- could be that we use an API call to generate N more examples, and then once we have 3/5/etc, we stop the generative process and move to the next phase.
- we also need to get the system to be fixed slowly, perhaps line by line. It would be best to generate the intentionality of each line fix and turn that into text, which we can process in the next phase.
- while the system is fixing it, use the metadata about how it's going to be fixed to create text-to-speech (https://itsfoss.com/espeak-text-speech-linux/) output for a narration of what's happening. (I DO)
- for the next iteration, generate a similar scaffold and have the system pause a bit longer so the user can follow along. (WE DO)
- at the end of the second iteration, invite the user to try it themselves, potentially with a third autogenerated, but incomplete, example.
- see about doing the fix and narration inside of a server, but record it (cypress/puppeteer/etc), and output a video of that happening.
- automate the upload of the video to youtube.

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



## 22) What to Expect when you're Expect-ing
- simple static page that shows which APIs go with which
JS assertions library (chai/expect/enzyme/etc)

## 23) CBMC in Docker container
- need to test form of inputs/outputs
- programmatically remove particular methods and ask the user
to write a method to replace it...give feedback on whether the
user's method "functions the same"


## 30) Turn Stress in the Speech Stream into a Python module to take in a word and output the reasons why it has a given pronunciation
- key syllable
- prefixes
- affixes
- origin of the root



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

## 90) Make simple micromaterial to show how to calculate resource reservation
- https://medium.com/@vlad.fedosov/how-to-calculate-resources-reservation-for-ecs-task-3c68a1e12725
- (X / 100) * Y * 1.3)
where:
* X — current CPU utilization (percentage)
* Y — value you specified in Task parameters
* 1.3 — buffer capacity you want to reserve for workload spikes (Note: 1.3 value may not fit everyone’s needs, it’s just a baseline)
- knowreservations.netlify.com

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
- probably just drag and drop "tasks" into VMs to watch how mismatches might throw specific errors: unable to place task because no container instances met all of its requirements
- see if anyone on awsnewbies or cloudnewbies finds this useful

## 123) Micromaterial to practice creating an allow list via regex for web form validation
- ideally with a bunch of inputs listed and asking for a regex that would allow through only the ones we know we want
- possibly more rather than less hand-holding, though also make this configurable

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


## 129) Create a corpus of content on various docs sites
- MDN docs
- AWS docs
- GCP docs

## 130) Use Ben's lidar thing to visualize tcp traffic going between containers
- containers since you can have fine-grained control over tcpstuff without needing anyone to install anything except docker
- needs lots of exploratory data analysis, since I'm not even sure what things are going to be interesting
- possibly look at the tcp traffic involved in a basic rails app (frontend/backend/database), and be able to filter for stuff(?) in the browser
- make it more of an "art project" and create graphics based on different common web framework demos (rails/gin/express/flask/etc)

## 130) Use tensorflow JS to make a Simon Says for simple English practice
- calculate where people's hands are and give simple commands (either written or audio) like "move your left hand up", "move your right hand down", or "keep both hands up".
- give automated feedback about whether they did it correctly.
- we don't have any depth information, just 2D, so have to stay with up/down/left/right.
- Possibly create a game interface, where two people "compete" for longest streak, and take turns holding the phone.


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
- if we run this in k3s, we might be able to use a web UI to send requests to a backend that directly updates config via kubectl.

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

## 145) Homelab network expansion
- get one pi for just prometheus/grafana
- we need somewhere for a git server (gitea/gogs/etc)
- we need somewhere for an ArgoCD cluster to run
- we need somewhere for OSSEC to run
- fire up three VMs on the mini (also decide what to put in three VMs)
- step though https://grafana.com/blog/2019/08/22/homelab-security-with-ossec-loki-prometheus-and-grafana-on-a-raspberry-pi/

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

## 153) Investigate using opentelemetry for micromaterials
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

## 160) Code Corpus API
- we've got data sorted with https://github.com/lpmi-13/code-corpus-collector
- we need a list of things people would want to use this for
- for now, we can do without update of the data...just cause there's already enough to keep us going for a while
- we probably need a landing page at the main domain (codecorpus.net), and then have the api respond at the subdomain `api.codecorpus.net`.

## 161) Use the shift-fuzzer-js for creating random function declarations
- figure out something to do with this
- https://shift-ast.org/fuzzer.html

## 162) See how much this (or things like this) could be made into a gitpod-based workshop
- https://gist.github.com/jedrichards/9942165

## 163) Create learning space for Rana Khalil's security stuff
- https://ranakhalil.teachable.com/p/web-security-academy-video-series
- other stuff she does

## 164) Create learning space for the 90 days of devops github repo
- https://github.com/MichaelCade/90DaysOfDevOps

## 165) Create corpus of transcript/audio for Darknet Diaries
- How to talk like an infosec person
- Will need lots of exploratory data analysis to see what falls out
- https://www.youtube.com/watch?v=RrH4qOYt6P0&list=PLtN43kak3fFEEDNo0ks9QVKYfQpT2yUEo

## 166) Create a single serving webpage that provides "people shout at you during your live coding tech test" as a service
- two people on the call
- maybe a third one joins midway?
- recorded separately with colorful costumes
- spliced together and served via a single webpage

## 169) Micromaterial to practice using tc
- traffic control...simulate dropped packets and corrupted packets and all kinds of network issues.
- this would be a better tool to see what happens when network conditions change, as opposed to actually debugging things, since you wouldn't normally encounter running tc in a production system.


## 172) Make a codewords implemenation
- based on https://github.com/jaredreisinger/react-crossword
- then take away clues
- then get a dataset for the words
- then decide on how to organize the dataset for each letter occurring how many times (or whatever codewords uses)

## 173) List of all public GitHub repositories
- available at https://docs.github.com/en/rest/repos/repos#list-public-repositories
- with an auth'ed user, we can get 5,000 requests per hour (with 100 results per request), which means it'll be about 41 days to grab everything.
- store the repo ID, since that's what we paginate by, and it also means we can just query the diff later.
- put this in a container and probably run it on the mac mini (since I'm doing literally nothing with it).
- storing just the URL and the ID should be around 300MB for all 492 Million repos (based on testing in the browser).

## 174) Create a docker container for computing item analysis
- start with https://github.com/patriciamar/ShinyItemAnalysis
- semi-working prototype at https://github.com/lpmi-13/item-analysis

## 175) Use gdb (probably in a gitpod) to analyze core dumps
- start with https://www.brendangregg.com/blog/2016-08-09/gdb-example-ncurses.html
- also work out what issues we would expect to see trigger core dumps
- see if you can find a corpus of core dump data

## 176) Add recursion detection to corpus collection
- https://docs.python.org/3/library/inspect.html#inspect.getclosurevars to find all the recursive functions (maybe there's also a simpler way)

## 177) Figure out a micromaterial for the We Hack Purple stuff
- https://wehackpurple.com/pushing-left-like-a-boss%E2%80%8A-%E2%80%8Apart-5-10%E2%80%8A-%E2%80%8Auntrusted-data/

## 178) Micromaterial for just checking whether a site is vulnerable to CSRF
- JWT in auth header, not vulnerable
- passed in cookie, could be vulnerable
- a relevant action (maybe ask for clarification on this)
- no unpredictable request parameters (maybe this just means not ignoring unexpected params)

## 179) Micromaterial for fixing relative imports in python
- just set up a simple app in gitpod that doesn't work because the imports are bad
- then fix them
- also do this for golang (separate repo)

## 180) Micromaterial to set and grep for correlation ID
- set random UUID's in the HTTP request headers, and track a transaction across different services
- set something like X-Correlation-Id
- possibly start out with a problem in some 3-service (or whatever number) architecture, and then add in the correlation ID and check logging in Kibana to see where the problem is

## 181) See about converting common leetcode questions to things that are more "social" (ie, involving people)
- https://en.wikipedia.org/wiki/Wason_selection_task#Explanations_of_performance_on_the_task
- Cosmides and Tooby (1992) and found instead that "performance on non-arbitrary, evolutionarily familiar problems is more strongly related to general intelligence than performance on arbitrary, evolutionarily novel problems"

## 182) Micromaterial to supply the missing part of recursive functions
- this is going to be HEAVILY focused on the tests
- basically have the tests completely specify the scenario (how many "things" are adjacent)
- the recursive functions could be partially complete, or even just have the function name defined, with nothing else
- put it in gitpod, naturally
- do it in typescript and/or python

## 183) Web app to let groups of learners submit summaries for a method/function in an open source repo
- needs a login, so we can group people by class/cohort/etc.
- this way, we probably don't need to worry about content moderation
- group owner (the person who sets up the group) can send invites and allow people to join, or also make other members owners
- users submit summaries (short) of functions, and they can also read the summaries that other users in the same group have written.
- natural activity to complement a learning space for a small cohort of learners

## 184) Micromaterial to present faded code blocks
- possibly fade out the keywords, or some other aspect of a working program.
- the benefit of putting this in a runtime environment is you can probably even add tests, and when you've "unfaded" the code, the tests pass
- we also get feedback from whether it runs/errors.

## 185) Trainline PR choose your own adventure
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

## 187) Micromaterial to practice back-of-the-envelope calculations
- How many characters does your GUID need? Eg, for a given number of users, a given number of items in a database, a given number of X to keep track of...
- Capacity estimates and constraints
- traffic estimates (breakdown between read/write in difficult mode, just total traffic/requests in easy mode)
- queries per second (per minute?)
- storage estimates (number of "things" to storage, and total storage space needed)...maybe also consider if we want to keep data for X years
- bandwidth estimates (how many requests per second * size of request)
- memory estimates (in case of caching)
- how much percentage of the requests should we cache (figure out number of requests and then how many of those requests we expect to hit the cache)


## 188) Chaos-pod
- controlled chaos in a gitpod
- we need the smallest possible bunch of stuff that we can deterministically break (network partition, load, and maybe bad config updates)
- use github.com/wg/wrk to generate load
- use tc to simulate network partitions
- simulate new deployments of config maybe
- possible issue that we can abstract away the actual configuration of the issues via a web UI (so that "setting" security group rules "looks" the same in our pod as it does in an authentic situation), but then the interrogation of what the actual issue is could get a bit muddled, and the implemenation will be WAY heavier...
- use the `stress` command to simulte CPU/IO/Memory stress https://lindevs.com/install-stress-command-on-ubuntu

## 189) AR for cubetto thing
- just make something with AR Kit for react native
- if possible (and it actually works and stuff), see about joining the iOS dev program, just to get experience with that whole fiasco

## 190) ShouldIPartitionIt (maybe .com)
- a webapp (map, not territory) to examine what happens if you have a given data schema and decide to partition on different parts of it
- intent is to _show_ how parititioning on things with higher variation (eg, users' location) is "better" than paritioning on things with lower variation (eg, users' gender).
- could we include the idea/visualization of a "hot" partition?

## 191) MySQL/PostgreSQL Dojo
- a simple micromaterial (similar to the mongo dojo) to practice common tasks in a MySQL database.
- could be that we really just care about is just seeing different failure modes for this database, so maybe we just set up a containerized database with prometheus and grafana to monitor, then create different ways to load it to failure
- one fun way to do this would be the web UI + k3s cluster + BOOM
- what happens to running queries when the process that initiated them dies…does MySQL get a signal to stop the query, or does it just run forever?
- add in stuff from https://blog.lawrencejones.dev/isolation-levels

## 192) Elastic Dojo
- simple micromaterial to see how/when Elastic search fails
- could be that without sufficient scale, it's not possible to learn anything meaningful, but I also have never done anything with ES management, so anything here would result in learning stuff I don't know now.
- We should see if we can add some filter tuning in here... https://www.elastic.co/blog/found-optimizing-elasticsearch-searches
- Also would be cool to practic performing a re-index in different scenarios without downtime: mapping change, cluster upgrade between major versions, etc

## 193) Overload Scenario
- originally conceived of as just mimicking Black Friday, but it could be that this is very similar to the dojos anyway.
- maybe the best learning would just be researching and documenting the different ways to create load, and also looking at the tradeoffs of low per transaction data througput but high transaction volume VS high data payloads per transaction with slightly lower transaction volumes.
- the whole point would be to tease out what a bunch of terms (eg, "iops", "throughput", "saturation") mean in practice, and experiment with how we would create different conditions affecting those things.

## 194) Debugging Checklist
- basically, I keep forgetting simple things while debugging (like checking thequotes), so I need a checklist to remind me of the super simple stuff to check
- quotes
- spelling
- white space
- is it on?
- etc

## 197) Get some simple micromaterials (maybe one that branches off?) for Julia Evans Linux Debugging Zine
- awesome tools in here and great examples, so put some of them into exercises

## 198) How to talk like an SRE
- grab audio/transcripts from https://www.oncallmemaybe.com/
- grab audio/transcripts from https://sre.google/prodcast/
- grab audio/transcripts from https://smallbatches.fm/episodes (this one might not be as relevant)
- this one only has transcripts in youtube, but we can grab that and the audio in one place (plus the API might be nicer than webpage scraping) https://www.youtube.com/@SlightReliability


## 200) Will it fire?
- Micromaterial to practice going from a graph with alerting settings to deciding if it would fire or not
- include evaluation period, evaluation frequency, cooling off period, and stuff like that
- have a simple auto-generated graph and the settings below it and answer the question "would this fire?"

## 201) AwkSedFred
- basically the same as JQ-pilot, but do it for parsing and processing with both awk and sed
- could be log lines, could be other types of text
- exercises with just awk, just sed, and combining both
- could we do something with streaming?
- main issue is going to be how to visually present the exercise, since we don't have enough screen real estate (especially on mobile) to really show a lot of line)
- could we do something with putting data into kibana? Do people parse kibana stuff with CLI tools? I don't assume so, since it's a GUI, but who knows.

## 202) Generate transcripts with Whispernet (or is it just Whisper)
- whatever that sweet tool is to generate transcripts from audio would be very cool to play with. See about leveraging it to create a corpus of certain genres in tech talk.

## 203) specifically network-based micromaterial
- using one or more of https://www.brianlinkletter.com/2023/02/network-emulators-and-network-simulators-2023/
- cloud agnostic, more about routing, packet inspection, protocols and subnets
- https://www.reddit.com/r/devops/comments/15w9a1d/comment/jxaod5y/
- https://www.reddit.com/r/devops/comments/113qdft/comment/j8rwlwa/ (specifically the error messages distinction bit)

## 204) Auth0 Dojo
- I need to build more flows where things authenticate with other things, and ideally I can have one single micromaterial that does at least one or more of the following:
- allow a frontend to log somebody in via SSO (google/GitHub/etc)
- integrate with Auth0 to grant an API token, and then validate that token (somehow) before granting access to resources
- something with JWTs (which might be connected to the stuff above, but again, this is why I need the Auth0 dojo)
- this could be done _without_ Auth0 necessarily, but their docs are super nice, so would be easy to get to grips with, and hopefully help cement some concepts.
- a backend integration that deals with Auth0 something something...


## 208) Ideas for things that need more focused practice
- creating a service mesh
- performance profiling code in a running container (eg, in production)
- setting up firewalls correctly
- network peering (VPC or otherwise)
- setting up an observability pipeline (maybe just ELK though)
- pentesting known vulnerable applications (WebGOAT, OWASP, etc)
- pentesting fundamentals like the entirety of Black Hat Python, but in running VMs (possibly gitpod, iximiuz, etc?)
- simple updates to make an app production-ready (containers, instrumentation, logging, etc)

## 209) General DevOps skills to find use cases for (and then create micromaterials for)
- port forwarding (either in simple containers or k8s)
- attached to a process in a different container (application profiling in k8s)
- if a pod is stuck in pending state,  how would you troubleshoot?   what might be the problem?  (cluster autoscaler, taints/tolerations)
- a legacy app is in crashloopback, it takes a long time to startup and it's failing it's health checks / being restarted before it gets a chance to initialize.  what can we do to allow this app to startup correctly?
- followup: how do you determine if a pod is healthy or not?  what are the three different probes for and when would you use them? (startup, liveness, readiness)
- use cases for initcontainer

## 210) Distributed tracing in a microservice architecture (related to #180)
- set up a bunch of different microservices (auth/logging/billing/users/etc)
- wire up the logging
- add in some tracing
- practice following the traces through the app
- possibly also simulate some problems that we can find the bottlenecks in (latency + perf profling maybe?)
- see if we can use https://github.com/hansehe/jaeger-all-in-one

## 211) custom GPT Micromaterials Assistant
- get the assistant to be able to discriminate between a brainstorming request, when it can just respond with short suggestions, and a longer description of the process that it's planning to use (eg, to set up a micromaterial that's focused on k8s logging debugging).
- ask the assistant to be able to provide pratical steps to follow while debugging/troubleshooting, and also have it express those in discrete small steps.

## 213) Index impacts
- Add a few different indexes (maybe even just have a few scripted so the user doesn't need to decide which indexes to try) and see what the impact is across other measurements (inspired by Observability Engineering, 2022)
- Is the main query scanning fewer rows than before or more?
- How often is the new index being chosen by the query planner, and for which queries (this implies that we have a number of different read operations being executing continuously against the database)
- Are write latencies up overall, on average, or just at the p95/p99s? (we'll also need some background write operations to measure this)
- Are queries faster or slower with this new index
- What other indexes are also used along with the new index (assuming index intersection)
- Has this index made other indexes obselete (need to work out a good way to measure/show this)


## 217) specific index investigation
- based on [this thread](https://twitter.com/mikecodemonkey/status/1787973145523274169?t=CcylBV0U_jmWcEFFFYcmyA&s=19), set up a simple web app that loads things (users, accounts, reviews, whatevers), but it loads super slow
- query is select count(\*) as `numrows` from `user_logs` where `date` >= '2024-04-07' and `date` < '2024.05-07' and `event` = 'login' and `client_id` = SOME_CLIENT_ID
- involves indexes on "date", "event" and "client_id"
- see in an explain query that mysql is merging the indexes and has to deal with all the rows
- goal is to cut out as many rows as you can as fast as you can
- composite index needs to be in the right order (most selective equality first, so client_id here), and range condition last (date, in this example).
- order of WHERE clauses doesn't matter (MySQL optimizes this anyway), only order of indexes in the composite index...so we can have date first in the where even though it's last in the composite index
- this should be about a 950x improvement.

## 218) Troubleshoot keep-alive issues
- based on https://iximiuz.com/en/posts/reverse-proxy-http-keep-alive-and-502s/
- set this up in a place where we can reproduce the issue...start with ludicrous values for the keep alive on the application end, like 20 ms or something, and update the setting for the load balancer (preferably traefik) to be closer to 2 seconds (default is 3 minutes). In theory, if the values are way out of wack, we should be able to reproduce even without super high traffic loads, which will be more challenging locally.
- another way to do it would be to introduce artificial latency via `tc`, and run that in either gitpod or iximiuz.
- also https://www.tessian.com/blog/how-to-fix-http-502-errors/
- https://github.com/h2o/h2o/issues/281 has good troubleshooting steps
- for node-specific issues, https://stackoverflow.com/questions/45626787/nodejs-application-behind-amazon-elb-throws-502, and https://stackoverflow.com/questions/12651466/how-to-set-the-http-keep-alive-timeout-in-a-nodejs-server
- good simple post https://shuheikagawa.com/blog/2019/04/25/keep-alive-timeout/

## 219) Replay optimizing CI
- based on https://owaiskhan.me/post/improve-ci-build-time-and-reduce-cost.html
- as with everything, measure first, then optimize, then measure again (ideally at each step).
- the actual learning objective is moreso around how to measure whether changes are improvements or not...the above repo is a rails build, and also uses Circle-CI, so it could be that with other combinations (eg, Node + GitHub Actions) that some things aren't actually improvements, so the practice in measuring is definitely the main takeaway.
- depending on how many times we intend for users to run CI, then measure, then change, then re-run...it might mean that they use up the build-minutes quite quickly, so keep an eye on that.
- ...possibly turn this into a blog post with long-form explanation of stuff tried (especially since I'm probably gonna do this with Node instead of rails).

## 220) Turn Linux Perf Analysis blog into micromaterial
- https://netflixtechblog.com/linux-performance-analysis-in-60-000-milliseconds-accc10403c55

## 221) Simple Webapp to demo different "catch" behavior
- it's confusing what we should put in the `catch` block of a javascript `try/catch` block, so we should have some examples available in source code (and show it in the UI), alongside the behavior that the user sees.
- based on https://x.com/vponamariov/status/1795122912627695817?t=HyuLmYIAIEHvTyCkAFGutA&s=19
- log something out for later investigation, but don't show an error to the user
- present a dialog in the UI for the user to try again
- don't catch anything, and the error shows up in the console.log
- automatic retry something (async call to a backend) and don't show anything to the user
- for the unanticipated edge case, just a default "something went wrong, please try again later" message to the user.
- for another approach to unanticipated edge case, just display to the user what the error was (this is likely to be stacktrace gibberish).
- also potentially discriminate between 4xx/5xx

## 222) Generate minimal pairs with AI

- use https://github.com/coqui-ai/TTS to generate a bunch of minimal pairs via AI-generated voices.
- in theory...we could also take transcripts that have a bunch of minimal pairs (this would basically be any large enough corpus or normal speech), pick out the minimal pairs, and then just change the voices, a la Drake AI songs.

## 223) Distributed Dojo
- this might be just one thing, or it might be decomposed into multiple smaller things...
- retrying
- queueing
- caching
- load shedding
- sharding
- potentially start with a monolith system and practice decomposing it...or maybe we have a distributed system that does none of these things and we need to add them in in order to make it better/smoother/faster/stronger.

## 224) Fixing memory leaks in nodeJS
- https://marmelab.com/blog/2018/04/03/how-to-track-and-fix-memory-leak-with-nodejs.html
- if feasible, figure out how to get this into gitpod/iximiuz/other

## 225) things to speed run on iximiuz 

- https://itnext.io/distributed-tinyurl-architecture-how-to-handle-100k-urls-per-second-54182403117e

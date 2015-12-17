# listeningtestapi
A simple PHP api for audio preference test

## Usage 
### Step 1: Prepare your files in the following format
```
X1_a1.mp3
X1_a2.mp3
X2_a1.mp3
X2_a2.mp3
```
where X1, X2, etc. are conditions and a001, a002, etc. are example numbers. 
For example in speaker identification test, the conditions are names such as
"Adam" and "Bob". If there are 5 utterances used in this test, we have 001 to 005
for utterance numbers. If we also want to test if the subject is paying attention,
we can introduce validation voice spoken by "Catherine" (Cat for short). 
In this case the file names should be
```
Adam_001.mp3
Bob_001.mp3
Cat_001.mp3
...
Adam_005.mp3
Bob_005.mp3
Cat_005.mp3
```

### Step 2: configure your test
In file config.js, modify config. We support two types of tests: 

(1) XAB test where a reference track is presented and a subject is asked to choose one of the two target tracks
(2) preference test where there is no reference track

In the above example, where preference test should be conducted, the config struct might look like the follows:

```
config = {
  "reference" : 0            // no referece
  "condition_type" : [1, 1]  // randomize name and utterance
  "held_out" : ["Cat"]       // Cat condition is excluded in the test
  "validation" : ["?", "Cat"]// validation is between "Cat" and any other voice
  "validation_count" : 4     // 4 validation tests per batch
  "test_count": [1, 3]       // use one condition pair ("Adam" vs. "Bob") and three utterances
}
```

Message For TAs:
Problems Faced While Executing This Project:
1) Not able to use required dataset Timit as it has paid version.
2) Downloaded one Timit dataset from different source but not able to load it in the program due to structural issues of the data folder.
3) Then diverted our dataset to Librispeech but took lot of time to download entire dataset even if need to use only 100 hrs or 10 hr labeled.
4) Loaded dataset finally tokenization also completed but not able to run the training function as there was certain dependency libraries like conda, pillow, open cv which versions were not matching and was not able to download the required distribution with our current Python environment.
5) Also as the program was supposed to run on Timit dataset also made certain changes to work on Librispeech but not able to succeed with proper entire execution of program worked with preprocessing of dataset i.e. blanks addition between letters of each word, adding wild card symbol, tokenization, due to above point not able to finish the execution.

<https://github.com/huggingface/transformers/tree/master/examples/research_projects/wav2vec2>.

You need to have libsndfile installed in the system:
```bash
apt-get install libsndfile-dev
```

To run:
```bash
pip install -r requirements.txt
for r in {0..9}; do bash script.sh 0.$r; done
```
Here "0.$r" controls the ratio of masking on the labels.
It takes a value between 0 and 1.
When it's 0.0, no masking (label is clean).
When it's 1.0, the whole label is masked.

The script loop "0.$r" from 0.0 to 0.9, and reproduce the ASR experiment using WCTC.

##
If you want to use the standard CTC instead of WCTC, change the line 6 in script.sh:
```
export WCTC=True
```
to
```
export WCTC=False
```

## Settings to reproduce ASR experiments
We use learning rate = 1e-4, effective batch size = 32, train 50 epochs.
Other settings can be found in script.sh and the paper appendix




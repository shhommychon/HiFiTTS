GENERAL INFORMATION:
===================

Hi-Fi Multi-Speaker English TTS Dataset (Hi-Fi TTS) is based on LibriVox's public domain audio books and Gutenberg Project texts. 

Version: v_0
Sampling Rate: 44.1 kHz
Bit Depth: 16 bits

Note:
- The LibriVox audio files are recorded by volunteers. Despite the careful selection of the readers and their books, the audio quality of the LibriVox recordings is still lagging behind professional audio recordings. For example, we observed that some samples have a narrow signal bandwidth althouth the sampling rate is 44.1 kHz (see books_bandwidth.tsv).
Note, the final book bandwidth evaluation differs slightly from the approach described in the paper. Here, after the segmentation and audio post-processing, the values for the whole book were calculated and averaged. Originally, we evaluated book bandwidth using 30 seconds from a single chapter.
- Some readings are artistic, i.e. readers might change their voices depending of a book character.
- No silence trimming was done on audio segments.


MANIFEST FILES
==============

Each Reader_Id (RI) has a separate manifest for each data SPLIT (train, test, and dev).
Audio_Quality (AQ): clean or other.

Manifest naming convention: RI_manifest_AQ_SPLIT.json

Manifest files contain: 
  - audio_filepath: path to the audio file, 
  - duration: audio file duration, 
  - text: pre-processed text (text lowercased, punctuation removed),
  - text_no_preprocessing: original text, 
  - text_normalized: normalized text (abbreviations and non-standard words are expanded to their full spoken equivalent, punctuation marks were normalized to be consistent accross the texts).


DIRECTORY STRUCTURE
===================

.
├── 11614_manifest_other_dev.json                                 # Manifest file for RI: 11614 AQ: other SPLIT: dev
├── 11614_manifest_other_test.json                                # Manifest file for RI: 11614 AQ: other SPLIT: test
├── 11614_manifest_other_train.json                               # Manifest file for RI: 11614 AQ: other SPLIT: train
...
├── 9017_manifest_clean_dev.json                                  # Manifest file for RI: 9017 AQ: clean SPLIT: dev
├── 9017_manifest_clean_test.json                                 # Manifest file for RI: 9017 AQ: clean SPLIT: test
├── 9017_manifest_clean_train.json                                # Manifest file for RI: 9017 AQ: clean SPLIT: train
...
├── books_bandwidth.tsv                                           # Bandwidth estimation for each book
├── LICENSE.txt                               	                  # License file
├── readers_books_clean.txt                                       # List of LibriVox Readers and their books included in the CLEAN Set
├── readers_books_other.txt                                	  # List of LibriVox Readers and their books included in the OTHER Set
├── README.txt                                                    # This README file
└── audio                                                         # Folder with audio files
    ├── 11614_other                                               # Audio files for RI: 11614 AQ: clean
    │       ├── 10547                                             # LibriVox BOOK ID
    │             ├── thousandnights8_04_anonymous_0001.flac      # Audio file in FLAC format. The name of the audio file contains chapter name and segment id
    │             ├── thousandnights8_04_anonymous_0003.flac
    │             ├── thousandnights8_04_anonymous_0004.flac
    │             ├── thousandnights8_04_anonymous_0005.flac
    │       ├── 11736
  ...     ...
    │       └── 14179
  ...
    ├── 9017_clean
    │       ├── 11216
    │       ├── 13089
    │       ├── 13130
	...     ...



STATISTICS
==========

The corpus is split into clean and other sets based on audio quality. 
The clean set includes recordings with high sound-to-noise ratio and wide bandwidth.
The books with noticeable noise or narrow bandwidth are included in the other subset.
Some readers are present in both sets since the audio quality is not consistent across reader's books.

╔═══════════╤═════════════════╤════════╤════════════╤════════════╤════════════╗
║ Reader ID │ Reader Name*    │ Gender │ Clean, hrs │ Other, hrs │ Total, hrs ║
╠═══════════╪═════════════════╪════════╪════════════╪════════════╪════════════╣
║ 92        │ Cori Samuel     │ F      │ 27.3       │            │ 27.3       ║
╟───────────┼─────────────────┼────────┼────────────┼────────────┼────────────╢
║ 6097      │ Phil Benson     │ M      │ 30.1       │ 3.4        │ 33.5       ║
╟───────────┼─────────────────┼────────┼────────────┼────────────┼────────────╢
║ 9017      │ John Van Stan   │ M      │ 58.0       │            │ 58.0       ║
╟───────────┼─────────────────┼────────┼────────────┼────────────┼────────────╢
║ 6670      │ Mike Pelton     │ M      │            │ 17.7       │ 17.7       ║
╟───────────┼─────────────────┼────────┼────────────┼────────────┼────────────╢
║ 6671      │ Tony Oliva      │ M      │            │ 24.1       │ 24.1       ║
╟───────────┼─────────────────┼────────┼────────────┼────────────┼────────────╢
║ 8051      │ Maria Kasper    │ F      │            │ 30.4       │ 30.4       ║
╟───────────┼─────────────────┼────────┼────────────┼────────────┼────────────╢
║ 9136      │ Helen Taylor    │ F      │            │ 24.3       │ 24.3       ║
╟───────────┼─────────────────┼────────┼────────────┼────────────┼────────────╢
║ 11614     │ Sylviamb        │ F      │            │ 22.2       │ 22.2       ║
╟───────────┼─────────────────┼────────┼────────────┼────────────┼────────────╢
║ 11697     │ Celine Major    │ F      │            │ 26.8       │ 26.8       ║
╟───────────┼─────────────────┼────────┼────────────┼────────────┼────────────╢
║ 12787     │ LikeManyWaters  │ F      │            │ 27.3       │ 27.3       ║
╟───────────┼─────────────────┼────────┼────────────┼────────────┼────────────╢
║           │                 │ TOTAL  │ 115.4      │ 176.2      │ 291.6      ║
╚═══════════╧═════════════════╧════════╧════════════╧════════════╧════════════╝
*Although the source material for the Hi-Fi TTS dataset is in the public domain, when we selected a voice sample for a text-to-speech (TTS) application we sought the written consent of the speaker.
We believe it is ethically responsible to get the speaker's consent before using their voice for synthetic replication and we strongly encourage other developers to seek such consent.

ACKNOWLEDGEMENT
===============
We thank Rafael Valle for his help with audio post-processing and his valuable feedback.

REFERENCES
==========

@article{bakhturina2021hi,
  title={{Hi-Fi Multi-Speaker English TTS Dataset}},
  author={Bakhturina, Evelina and Lavrukhin, Vitaly and Ginsburg, Boris and Zhang, Yang},
  journal={arXiv preprint arXiv:2104.01497},
  year={2021}
}

Original LibriVox audio files were split into short segments using the CTC Segmentation project by Ludwig Kuerzinger et al.:  CTC-Segmentation of Large Corpora for German End-to-end Speech Recognition https://arxiv.org/abs/2007.09127.

@InProceedings{ctcsegmentation,
author="K{\"u}rzinger, Ludwig and Winkelbauer, Dominik and Li, Lujun and Watzel, Tobias and Rigoll, Gerhard",
editor="Karpov, Alexey and Potapova, Rodmonga",
title="CTC-Segmentation of Large Corpora for German End-to-End Speech Recognition", booktitle="Speech and Computer", year="2020",
publisher="Springer International Publishing", address="Cham", pages="267--278",
abstract="Recent end-to-end Automatic Speech Recognition (ASR) systems demonstrated the ability to outperform conventional hybrid DNN/HMM ASR. Aside from architectural improvements in those systems, those models grew in terms of depth, parameters and model capacity. However, these models also require more training data to achieve comparable performance.",
isbn="978-3-030-60276-5"
}

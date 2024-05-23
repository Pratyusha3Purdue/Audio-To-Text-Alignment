# AudioToText Alignment
## Introduction
In this study we developed a methodology to align audio with corresponding text across multiple languages, focusing on non-dominant language communities. This research is crucial as it addresses the gap in language technology for diverse linguistic groups, enhancing inclusivity and accuracy in global communication. By leveraging a combination of phoneme generation and text alignment techniques, we created models that can accurately match spoken words to their written counterparts, even in languages with limited technological resources. Our approach involved rigorous simulations to test the robustness of our methods in various scenarios and several different languages. This innovative approach not only supports linguistic diversity but also paves the way for advancements in language technology, especially in underrepresented communities.

## Methodology

The model advances with audio tokenization, employing Wave2vec2/Soundstream to produce phonemes using the processed audio in the previous step, which are then transformed into textual transcriptions. SentencePiece processes these transcriptions to generate text tokens.  The tokens are then aligned with the pre existing subtitle(textual represtative) files of the audio files to check the accuracy of the model.

![image](https://github.com/Pratyusha3Purdue/AudioToText/assets/141969918/d6fd6a4d-18ff-404b-8d1e-a2ee65b2c412)






![image](https://github.com/Pratyusha3Purdue/AudioToText/assets/141969918/fba51e2e-60b2-41c5-aefb-890136e19508)

This step involves converting spoken language into a phonetic transcription, as shown by the model Wave2Vec2Phoneme. The waveform in above Fig  represents the audio signal for spoken words, segmented by phonemes. Each segment is marked to indicate the phonetic unit corresponding to specific parts of the speech waveform.
In this example, the word "cat" is phonetically transcribed as /k/, /æ/, and /t/. These phonetic symbols represent the distinct sounds of the word, demonstrating how the model breaks down spoken language into its constituent sounds for further analysis and processing.  
Following phonemization, the subsequent steps involve the utilization of phoneme sequences to train models for a range of linguistic tasks. By incorporating phonemes and their breakpoints, alignment tools like Eflomal can be fine-tuned to enhance speech synthesis quality, due to the model ability to process and interpret these fundamental sounds. Next, we came up with a validation metric and compared the output of the two models used for alignment. While Eflomal uses probabilistic techniques to learn word alignments from parallel corpora. Simalign, on the other hand aligns text by using a pre-trained multilingual language model. Hence it served as a good comparison metric to the model we built using Eflomal, which can be further trained to improve with more data. The future scope of this study involves assembling phonetic symbols into words by pinpointing word boundaries and aligning them with accurate transcriptions. This capability is particularly beneficial for the development of multilingual systems, allowing for more seamless and efficient integration of diverse language data, thus broadening the scope and applicability of language technology tools in global contexts.

       
## Model Architecture
Our approach utilizes a pre-trained model, trained on the Common Voice, as a foundation for subsequent experiments. We then employ focused experiments designed to address specific research questions regarding alignment model performance in the context of application to non-dominant languages. A key metric for evaluating these alignment models is the alignment error rate.

![image](https://github.com/Pratyusha3Purdue/AudioToText/assets/141969918/86513ed1-da33-4914-a7d9-45146cbe84d9)


## RESULTS
### Validation Metric:
The unalignment_ratio metric is calculated as follows:

**unalignment_ratio = (total_unaligned / sentence_length) * 100**

Here, total_unaligned is the sum of the unaligned words in both the target and source languages. This number includes any target words that don't have a corresponding source word (indicative of missing words in the source) and any source words without a matching target word (indicative of padding or extra words in the translation). The sentence_length is usually the length of the sentence in terms of the number of words in the source, target, or the longer of the two, depending on the specific implementation.

<img width="491" alt="image" src="https://github.com/Pratyusha3Purdue/Audio-To-Text-Alignment/assets/141969918/86362263-6b39-4812-9dda-dc4b31886884">


### Drawbacks of the unalignment_ratio Metric:
1.	Does Not Account for Misalignments: This metric only considers the presence or absence of an alignment but does not measure the accuracy of the alignments. A word could be aligned to the incorrect counterpart, and this metric would not capture such errors.
2.	Sentence Length Variability: If sentence_length is defined differently for source and target texts (for instance, using the longer sentence), it could skew the results. Languages with naturally longer or shorter sentence structures compared to their translation could unfairly influence the ratio.



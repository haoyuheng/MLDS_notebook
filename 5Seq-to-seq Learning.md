## 5	Seq-to-seq Learning

#### 5.1		Review of RNN

##### 5.1.1	RNN

A **recurrent neural network** (**RNN**) is a class of [artificial neural network](https://en.wikipedia.org/wiki/Artificial_neural_network) where connections between nodes form a [directed graph](https://en.wikipedia.org/wiki/Directed_graph) along a sequence. This allows it to exhibit temporal dynamic behavior for a time sequence. Unlike [feedforward neural networks](https://en.wikipedia.org/wiki/Feedforward_neural_networks), RNNs can use their internal state (memory) to process sequences of inputs. This makes them applicable to tasks such as unsegmented, connected [handwriting recognition](https://en.wikipedia.org/wiki/Handwriting_recognition)[[1\]](https://en.wikipedia.org/wiki/Recurrent_neural_network#cite_note-1) or [speech recognition](https://en.wikipedia.org/wiki/Speech_recognition).[[2\]](https://en.wikipedia.org/wiki/Recurrent_neural_network#cite_note-sak2014-2)[[3\]](https://en.wikipedia.org/wiki/Recurrent_neural_network#cite_note-liwu2015-3)

![img](/home/MLDS_notebook/assets/20170723211420228.png)

##### 5.1.2	LSTM( Long Short Term Memory )

In theory, classic (or "vanilla") [RNNs](https://en.wikipedia.org/wiki/Recurrent_neural_network) can keep track of arbitrary long-term dependencies in the input sequences. The problem of vanilla RNNs is computational (or practical) in nature: when training a vanilla RNN using [back-propagation](https://en.wikipedia.org/wiki/Back-propagation), the gradients which are back-propagated can ["vanish" (that is, they can tend to zero) or "explode" (that is, they can tend to infinity)](https://en.wikipedia.org/wiki/Vanishing_gradient_problem), because of the computations involved in the process, which use [finite-precision numbers](https://en.wikipedia.org/wiki/Round-off_error). RNNs using LSTM units partially solve the [vanishing gradient problem](https://en.wikipedia.org/wiki/Vanishing_gradient_problem), because LSTM units allow gradients to also flow *unchanged*. However, LSTM networks can still suffer from the exploding gradient problem[[22\]](https://en.wikipedia.org/wiki/Long_short-term_memory#cite_note-22).

![5-1](/home/MLDS_notebook/assets/5-1.png)

![5-1](/home/MLDS_notebook/assets/5-2.png)

##### 5.1.3	GRU( Gated Recurrent Unit )	

GRUs are lighter versions of RNN approaches than standard LSTM in term of topology, computation cost and complexity.

![5-3](/home/MLDS_notebook/assets/5-3.png)

![5-4](/home/MLDS_notebook/assets/5-4.png)

**The GRU requires fewer network parameters, which makes the model faster. On the other hand, LSTM provides better performance, if you have enough data and computational power.**






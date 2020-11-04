# Hw1

All different settings’ training was done using the same hyper-parameters:
•Epochs number = 100
•Optimizer = Adam
•Learning rate = 8e−4
When  evaluating  the  test  sets,  gradients  calculations  were  turned  off  (for  speedup),  and gradient descent was not applied.

## Dropout
A dropout with probability 0.2 was performed over all layers, except the final layer, whichwas a log-softmax layer in my case. For architectural simplicity, I applied the dropout function even for the non-Dropout settings, but with probability 0 (which effectively bypasses the dropout).Since during training the dropout accuracy isn’t indicative of the network’s actual accrucay(since 20% of the nodes are disabled), I re-evaluated the network’s accuracy over the training set after each epoch, but without dropout and without applying gradient descent. Thesame mechanism was applied for the test set evaluation.
## Weight Decay
For this setting only, the weight_decay argument of the Adam optimizer was set to 3e−3.

## Batch Normalization
Batch normalization layers were added the following way:
•One 2D batch normalization layer after the 2nd convolutional layer.
•One  1D batch normalization  layer after  each  fully-connected  layer (except  the  final layer).
After several sensitivity testings over the different arguments, it appeared that none had a truly  significant effect over the final results, so the default parameters were used  (epsilon= 1e−5,  momentum=0.1). For  evaluating  the test-set, the batch normalization parameters (γ,β) were kept static.

Osservando la chain rule notiamo che la derivata della funzione composta è uguale al prodotto delle derivate delle singole funzioni rispetto **all'input che hanno ricevuto**

- l'input di g() è x
- l'input di f() è g(x)

This has huge implication:

- the training of a neural network typically has a forward phase and a backward phase
- **during the forward phase we must save in memory all the intermediate activations AND weighted sums**
  - because during the backward phase we need to apply the derivative of the outermost functions (layers) wrt its input activation

**Training the network requires much more memory than just using the network for inference**

- inference requires only a forward pass
- we don't need to keep in memory the previous layer input activations

...

the derivative of the loss is just a product of derivatives, one for each layer (chain rule, composition becomes a rule)

...

when we go backward we transpose the weight matrix of the layer

- going backward we need to transform a vector with the dimension of the output with a vector with the dimension of the input
- this is the opposite transformation that happens in the forward pass

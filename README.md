# Neural_Network

The original model is composed by 3 parts:

* ADD-student: is a pretrained diffusion model that aims to synthetize the images in a few steps (1-4) starting from a noised version of the original image. So this model can use only from 1 to 4 iterations to denoise the input image. The parameters of this model are trainable.
* DM-teacher: is also a pretrained diffusion model but differently from the student, it can use a larger number of iterations to denoise the input. The parameters in this case are fixed.
* ViT Discriminator: is a pretrained Vision Transformer that is adapted to use as a discriminator with trainable parameters.

The key idea for the training procedure is:
starting from a real image, using a forward process, it introduces noise in the image obtaining a noised version $x_s$ of the original image.
The noised version is used as a starting point for the ADD-student model and using a denoising process it yields to a new image $x_\theta$.
This image is used both as an input to the discriminator model and as input to the teacher model.

# Neural_Network

The original model is composed by 3 parts:

* ADD-student: is a pretrained diffusion model that aims to synthetize the images in a few steps (1-4) starting from a noised version of the original image. So this model can use only from 1 to 4 iterations to denoise the input image. The parameters of this model are trainable.
* DM-teacher: is also a pretrained diffusion model but differently from the student, it can use a larger number of iterations to denoise the input. The parameters in this case are fixed.
* ViT Discriminator: is a pretrained Vision Transformer that is adapted to use as a discriminator with trainable parameters.

The key idea for the training procedure is:
starting from a real image, using a forward process, it introduces noise in the image obtaining a noised version $x_s$ of the original image.
The noised version is used as a starting point for the ADD-student model and using a denoising process it yields to a new image $x_\theta$.
This image is used both as an input to the discriminator model and as input to the teacher model.

<center>

![Baseline](https://miro.medium.com/v2/resize:fit:1400/0*cWVcA2VMGByT10qP.jpg)

</center>

## Instruction to run the code

To run the code, follow these steps:

* Open the notebook file .ipynb

* Specify the Dataset: Choose the dataset you want to test the model on. You can select either MNIST or FER.

* Download Pretrained Model: If you want to use the pretrained models, download them from the project's GitHub repository. These weights can be used to test the models without retraining.

  - To test the models using the pretrained weights, simply run the test section in the notebook and skip the training sections.

* Retrain the Model: If you prefer to train the models from scratch, do not import the pretrained models.

  - In this case, you need to execute all the training sections in the notebook to train the models anew.

By following these instructions, you can either test the models with pretrained weights or retrain them from scratch.

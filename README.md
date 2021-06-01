# Python-install-for-Machine-Learning-Tensorflow-Keras-Windows-10
Python install for Machine Learning (Tensorflow Keras) on Windows 10

###### What you will need :

- Windows 10
- Administrator rights

Hello! This post will aim at installing Python for Machine Learning with Keras on Windows 10.
At the end of this tutorial you will have installed the following:
- Python 3.7 (64-bit)
- Pip
- Tensorflow
- Keras
- Jupyter notebook

First, we need to install Python 3.7.9.
Download the Windows x86-64 executable installer at https://www.python.org/ftp/python/3.7.9/python-3.7.9-amd64.exe.

Install the program. Make sure you check the "Add Python to PATH" dialog box.

Open a Windows Terminal from Start >> All Programs >> Accessories >> Command Prompt and right click and choose "Run as administrator"

Check Python version by typing 
>python --version

It should read "Python 3.7.9".

Now install and upgrade pip (a Python package manager) by entering the following command
>python.exe -m pip install --upgrade pip

Once it is done, install Tensorflow. You will first need to install Microsoft Visual C++ Redistributable from the following link:
https://support.microsoft.com/en-us/topic/the-latest-supported-visual-c-downloads-2647da03-1eea-4433-9aff-95f26a218cc0

Then, install TensorFlow in the command line by typing
>python.exe -m pip install --upgrade tensorflow

# At this point, check that you are using Python 64-bit if Tensorflow install fail!!!

Then install Keras with
>python.exe -m pip install --upgrade keras

Finally, install jupyter
>python.exe -m pip install jupyter

Start a notebook with the command
>jupyter notebook

The jupyter notebook should open in your web browser. If it doesn't, copy paste the link in terminal that looks like
>http://localhost:8888/?token=31314d79ccf87a3d79cc377808db8cda06d84196887d0e0f

You can navigate in your file system. I will go to /Documents and then click on "New" and choose "Python 3".
![alt text](https://github.com/pleboulanger/Python-install-for-Machine-Learning-Tensorflow-Keras-Windows-7/blob/master/New_Python3.PNG)
It will create an Untitled python file.

Once it is done, you're good to go!
You can start writing your python code!

You can try to run the following "hello world"
```
import tensorflow as tf
mnist = tf.keras.datasets.mnist

(x_train, y_train),(x_test, y_test) = mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0

model = tf.keras.models.Sequential([
  tf.keras.layers.Flatten(),
  tf.keras.layers.Dense(512, activation=tf.nn.relu),
  tf.keras.layers.Dropout(0.2),
  tf.keras.layers.Dense(10, activation=tf.nn.softmax)
])
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

model.fit(x_train, y_train, epochs=5)
model.evaluate(x_test, y_test)
```

The result should be something like that (showing the training):

![alt text](https://github.com/pleboulanger/Python-install-for-Machine-Learning-Tensorflow-Keras-Windows-7/blob/master/Mnist.PNG)

You can add the following lines in order to see how well your model did on unseen data 
```
print (model.evaluate(x_test, y_test))
print (model.metrics_names)
```

The accuracy (acc) is your model's performance. 1 means 100%.

Congratulation, you just trained your first Deep Learning model!!

###### Sources :

Python
https://www.python.org/downloads/release/python-379/

Pip
https://pypi.org/project/pip/

Tensorflow
https://www.tensorflow.org/install

Keras:
https://keras.io/#installation

Jupyter:
https://jupyter.readthedocs.io/en/latest/install.html

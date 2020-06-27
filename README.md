# Stock price prediction with PyTorch using LSTM

 the data is for RELIANCE Stock Price From 2000 to 2020 
the target is to create LSTM  to predict the next day price

### based on the target the closing  price will only be considered 


# method 
sort the data by date
create new data frame that contain only the closing price  
 scale the new data frame by MIN MAX scaler in range of (-1:1)

set a sequence for training the LSTM and it was chossen to be 40 
create tensor that contain all sequence lists meaning the tensor will contain inner tensors each containg forty sequence
creating train and test data sequences by spliting by ratio 0.2 
 creating x and y data sets  the x will contain the first 39 elements of each inner tensor and the y will be the last element meaning the shape of x is (number of rows in it is data , 40-1=39= the first 39 elements , 1= the number of elements in each element which is one number presinting the price) 
 the y data shape is (number of rows in its data , 1: the last element of the 40 sequence ,1)

### each data will be converted to tensors as a requirement of the LSTM by torch 

# creating the LSTM
 defining the structore of the LSTM by setting the number of inputs which is one tensor the number of output which is one tensor and number of LSTM layers, the number of hidden units and dropout probablity 

### in the forward each LSTM will need hidden state and current state of memory which is initalized to zero in the forward 
### the output of the LSTM will give the output data and the new hiddden state and the new current state which are used with  .detach() to pervent the backprobagation to go all the way to the start meaning that it only foucus on recent memory 

the LSTM is followed by two linear neural networks 


## the next step is creating optmizer and criterion that will mean squared errore as it is regression problm


# training 

 for each of number of epoch the prediction will be calculate and the loss too which will be added to new list for graphing 
each step in the traing will required to set the gradinet to zero and  then apply it to update the optmizer



# getting the data on the original shape

to data it is required to inverse the MIN MAX scaler  which is done after the training 





# the next step is to caluclate the root mean square errore 


# the next step is to shift the data for the prediction to graph it along with original data  meaning the prediction of the training will start from day 40 and folowed by the test prediction


### the pervious step is shown in the last graph where the traing prediction will start after forty days and the y test will provide an info about the next day after the last period of the original data


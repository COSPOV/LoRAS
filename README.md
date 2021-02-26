# LoRAS
This repository provides an implementation of the integrated LoRAS algorithm for binary classification problems
### Usage guidelines
- The main function for LoRAS is LoRAS_gen. To generate LoRAS samples copy te code in the next cell and run the **LoRAS_gen** function following these guidelines.    

- The **LoRAS_gen** function takes and input the training data matrix and corresponding labels in form of numpy arrays. It is designed for only binary classificaion problems in version. Please make sure that the minority class labels are  set to 1.

- Other parameters are **convex_neighbourhood**, **shadow**, **sigma**, **num_RACOS**, **num_convcomb**

- **convex_neighbourhood** corresponds to the parameter k from the pseudocode in the original article. The standard value of this parameter shouldbe $5-10$. However for larger datasets (minority class size more than 500) it can be extended to 20-30.

- **shadow** corresponds to the parameter |S_p| from the pseudocode in the original article. The standard value of this parameter is to be kept around $100$.

- **sigma** corresponds to the standrd deviation for a Gaussian distribution to draw noise from. The standard value of sigma can be taken  as 0.005. Although in the original pseudocode it is proposed that a list of feature-wise sigma values is taken as input, we have noticed that a standard value of small enough sigma works quite well. 

- **num_RACOS** corresponds to the paramter [N_{gen}] from the original pseudocode. The standard value for this parameter is int(\frac{|C^T_{maj}|-|C^T_{min}|}{|C^T_{min}|}), where |C^T_{maj}|$ and $|C^T_{min}| are the number of majority and minority instances in the training dataset, that is provided as input to the **LoRAS_gen** function and the $int$ function refers to the gratest integer floor function in case \frac{|C^T_{maj}|-|C^T_{min}|}{|C^T_{min}|} is a float value. 

- **num_convcomb** corresponds to the parameter N_{aff} from the original pseudocode.


                                                               ::CAUTION::
                                                    
**The algorithm is most sensitive to the num_convcomb parameter. For high dimensional datasets with $F$ feature we highly recommend an user to optimize this parameter with values** [2, int(\frac{F}{4}), int(\frac{F}{2}), F], **and use the optimal parameter value, to get the best out of this algorithm.**

**Also, note that if you have normalized your data before training models please use a sigma value of 0.00000005**

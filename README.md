<div align="center"> 
  
# Improving-CNN-Performance

  [Click here to visit Google Colab](https://colab.research.google.com/drive/1JDfE_Nl8oCuQNhkDzR8hfQhLc-13WJeD?usp=sharing)

</div>

## A. Model Evaluation Analysis

1. What were the weakest-performing classes based on the confusion matrix? 
    Based on the confusion matrix and classification report, the weakest classes were the CapeGooseberry_plant (F1-score of 0.04), Tobacco_plant, and Red_Buffalo-Bur_plant, all of them showed near zero recall.

2. How did Precision, Recall, and F1-score vary across classes?
    The huge variation in metrics reveals that the baseline model suffered from class bias, where it labeled most images as "petunia" due to an inability to distinguish complex botanical features. This resulted in a high recall for one category while most others remained at 0.00, indicating the model was blind to 18 of the 20 plant species. 

3. What does a low recall indicate in your model?
    low recall means that the model is failing to identify the majority of actual positive instances for a class, effictively "missing" the plants it is supposed to detect.

4. How does AUC score reflect model performance compared to accuracy?
     While the accuracy was a poor 6%, the AUC scores (averaging 0.85) showed the model had a decent underlying ability to rank the correct class higer than the others, even if it wasn't the top choice.
   
B. Model Improvement

5. How did data augmentation affect validation accuracy?
    Data augmentation helped stabilize the learning process, preventing the model from hitting a fake 100% training accuracy and helping validation accuracy rise steadily.

6. Why is Batch Normalization important in CNNs?
    It is important because it normalizes the activation of each layer, preventing gradieants from becoming too small and allowing the deeper 8-layer architecture to train faster and more reliably.
    
7. What role did Dropout play in improving your model?
    Dropout acts as a regularizer by randomly disabling neurons, which forces the model to learn multiple independent features rather than relying on specific noise on the images.

8. How did Early Stopping prevent overfitting?
    Early stopping monitored the validation loss and halted training before the model could start memorizing the specefic details of the training set, thus preserving the generalization.

C. Performance Comparison
9. What improvements were observed after modifying the model?
    After training, the generalization gap decreased from a massive discrepancy to a synchronized trend where training and validation accuracy both moved toward the 40% mark.

10. Which enhancement contributed the most to performance improvement? Why?
    Data Augmentation contributed most because it directly addressed the lack of variety in the dataset, which was the primary cause of the initial overfitting. 

11. Did the gap between training and validation accuracy decrease? Explain.
    Yes, the gap decreased because the improved model focused on learning robust botanical features rather than memorizing pixels, bringing the training and validation lines closer together.
    
D. Explainability (Grad-CAM Integration)

12. How did Grad-CAM help in understanding model predictions?
    Grad-CAM helped provide a visual heatmap that revealed the baseline model was focusing on scattered bacground noise and edges rather than the actual plant features.

13. Did the improved model focus on more relevant regions? Provide evidence.
    The improved model showed more concentrated activations; evidence from the baseline Grad-CAM showed scattered hotspots, whereas the improved architecture's deeper layers filtered out background textures.

14. Why is explainability important in real-world AI applications?
    Expalinability is vital in real-world, such as agriculture, to ensure s=hte system is identifying a plant based on its leaves or fruits rather than irrelevant factors like the camera angle or the type of soil.


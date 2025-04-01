We measure how unhappy we are with how the current prediction turned out.
Loss has no kinda unit, different losses are not comparable. Like softmax loss of 2 and svm loss of 1.06 doesnt' mean svm is better.

Log Loss - Binary Cross Entropy
# Optimizing Loss
Optimization loss analogy is a blindfolded hiker. You want to reach the bottom of the hills. You can either try random directions around you and if it goes down - you step, if not - you stay. Or, more optimally you feel the slope with your feet (with gradient) and step where you feel the slope goes down. The learning rate represents the distance of your step, so you don't overstep the bottomest point.
## 📊 Comparison of the Three Approaches

This project evaluates three different SVM-based approaches for floor vs non-floor segmentation, focusing on both classification performance and computational efficiency.

---

### **Approach 1: Pixel-based Classification using RGB Features**

In this approach, each pixel is treated independently and classified using only its RGB color values. This method serves as a baseline but lacks spatial awareness and is sensitive to lighting variations.

- **Training Time:** ~70.7 seconds  
- **Accuracy:** 84%  
- **Weighted F1-score:** 0.86  

**Observation:**  
The model performs well on floor pixels but struggles to distinguish non-floor regions due to color similarity and the absence of contextual information.

---

### **Approach 2: Pixel-based Classification using RGB + Spatial (x, y) Features**

This approach extends pixel-based RGB classification by incorporating normalized spatial coordinates `(x, y)` as additional features. This enables the model to learn geometric priors, such as the likelihood of floor pixels appearing in the lower part of the image.

- **Training Time:** ~38.7 seconds  
- **Accuracy:** **89%**  
- **Weighted F1-score:** **0.90**

**Observation:**  
Adding spatial features significantly improves robustness and accuracy while also reducing training time compared to RGB-only classification.

---

### **Approach 3: Region-based Classification using Clustering + SVM**

Instead of classifying individual pixels, this approach groups pixels into homogeneous regions using clustering. Region-level features are then extracted and classified using an SVM.

- **Training Time:** **~0.02 seconds**  
- **Accuracy:** 85%  
- **Weighted F1-score:** 0.85

**Observation:**  
This approach achieves comparable performance with dramatically lower computational cost and produces smoother segmentation results.

---

## 🔍 Overall Summary

| Approach | Accuracy | Weighted F1 | Training Time | Key Strength |
|--------|---------|-------------|---------------|--------------|
| RGB (Pixel) | 84% | 0.86 | ~70.7 s | Simple baseline |
| RGB + (x, y) | **89%** | **0.90** | ~38.7 s | Best accuracy |
| Region-based | 85% | 0.85 | **~0.02 s** | Fastest & efficient |

---

## 🧠 Conclusion

The comparison highlights a clear trade-off between accuracy and efficiency. Incorporating spatial information leads to the best segmentation performance, while region-based classification provides significant speed improvements with only a minor reduction in accuracy. The optimal approach depends on the application’s accuracy requirements and computational constraints.

---

**Key takeaway:**  
Spatial context improves segmentation accuracy, while region-based methods offer major speed advantages with minimal performance loss.


Approach 2 (RGB + spatial) achieves the best overall performance by combining appearance and geometric information.

Approach 3 (region-based) offers massive computational savings with only a small drop in accuracy, making it suitable for real-time or resource-constrained applications.

Approach 1 serves as a baseline but is limited due to lack of spatial awareness.

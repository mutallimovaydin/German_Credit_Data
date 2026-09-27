# German_Credit_Data

| Metrika | Standart Threshold (0.5) | Optimal Threshold (~0.28) | Bank Standartı |
| :--- | :---: | :---: | :--- |
| **ROC-AUC** | ~0.78 | ~0.78 | > 0.70 (Kafi) |
| **Gini Əmsalı** | ~0.56 | ~0.56 | > 0.40 (Yaxşı) |
| **Recall (Pis Kreditləri Tutma)** | ~52% | ~81% | Mümkün qədər yüksək |
| **Precision** | ~61% | ~44% | Balanslaşdırılmış |
| **Gözlənilən Maliyyə İtkisi** | Yüksək (FN səbəbindən) | Minimum | Optimal xərc |

---

### Biznes Yekunu və Tövsiyələr (Executive Summary)

1. **Asimmetrik Xərc Optimizasiyası:** Standart 0.5 threshold-u əvəzinə asimmetrik xərc analizindən alınan optimal threshold-un tətbiqi, batıq kreditlərin (False Negative) payını kəskin azaldır və bankın ümumi kapital itkisini minimuma endirir.

2. **Əsas Risk Sürücüləri (Key Risk Drivers):**
   * `checking_status` (Cari hesabın balans vəziyyəti) və `duration` (Kreditin müddəti) riski əsas təyin edən faktorlardır.
   * Hesabında vəsaiti olmayan və uzunmüddətli kredit tələb edən müştərilər birbaşa yüksək risk qrupuna düşür.

3. **Skorkart İnteqrasiyası:** Qurulmuş 300–850 arası kredit balı sistemi əsasında avtomatlaşdırılmış qərar mexanizmi:
   * **Score > 650:** Avtomatik Təsdiq (Low Risk)
   * **550 < Score ≤ 650:** Əlavə Sənəd və ya Zamin Tələbi (Medium Risk)
   * **Score ≤ 550:** Avtomatik İmtina (High Risk)

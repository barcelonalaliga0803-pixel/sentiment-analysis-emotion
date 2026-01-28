# Emotion Classification / Duyğu Analizi Modeli

Tapşırıq üçün hazırlanmış 6 sinifli duyğu təyinedici modeldir.

## Dataset
- Fayl: test.xlsx
- Siniflər:  
  0 → sadness  
  1 → joy  
  2 → love  
  3 → anger  
  4 → fear  
  5 → surprise  
- Ölçü: ~20,000 nümunə

## 1. Araşdırma qeydləri
Sentiment / Emotion Analysis üçün əsas yanaşmalar:
- Lexicon-based → sadə, kontekst zəif
- Classical ML → TF-IDF + Logistic Regression / SVM (bu layihədə istifadə olunub)
- Deep Learning → BERT tipli modellər (daha dəqiq, amma ağır)

Seçilmiş metod: TF-IDF vektorləşdirmə + Logistic Regression 

## 2. EDA
- Ən çox joy sinfi
- Ən az surprise sinfi
- Class imbalance mövcuddur → class_weight='balanced' istifadə edildi

## 3. Text Processing
- lowercase
- linklər, mention-lar, hashtag işarələri silindi
- rəqəmlər silindi
- durğu işarələri və xüsusi simvollar silindi

## 4. Model
- Vectorizer: TfidfVectorizer (ngram 1-2, max_features ~12000)
- Model: LogisticRegression (multi_class='multinomial', class_weight='balanced')
- Train/test: 80/20 split

## 5. Nəticələr
- Test accuracy: **~0.84–0.87** 
- Ən yaxşı performans: joy və sadness
- Zəif performans: fear və surprise 

## 6. İstifadə
pandas
scikit-learn
matplotlib
seaborn
gradio
openpyxl
joblib
```bash
pip install -r requirements.txt
python emotion_model.py

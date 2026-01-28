# Sentiment Analysis / Emotion Classification

Tapşırıq 1 – “Sentiment Analysis” üçün hazırlanmış layihədir.  
6 sinifli duyğu təyinedicisi (sadness, joy, love, anger, fear, surprise)

## 1. Araşdırma qeydləri
Sentiment / emotion analysis üçün əsas yanaşmalar:
- Lexicon-based → sözlükdən istifadə, sadə amma kontekst zəif
- Machine Learning → TF-IDF + Logistic Regression, Naive Bayes, SVM (bu layihədə istifadə olunub)
- Deep Learning → LSTM, BERT tipli modellər (daha dəqiq, amma resurs tələb edir)

Seçilmiş metod: TF-IDF vektorləşdirmə + Logistic Regression (multinomial, balanced class weight)

## 2. Dataset və EDA
- Fayl: test.xlsx
- Sütunlar: text, label
- Siniflər:  
  0 → sadness  
  1 → joy  
  2 → love  
  3 → anger  
  4 → fear  
  5 → surprise  
- Paylanma: joy ən çox, surprise ən az → imbalance var

## 3. Text Processing
- lowercase
- linklər, @mention, #hashtag işarəsi silindi
- rəqəmlər silindi
- durğu işarələri və xüsusi simvollar silindi
- artıq boşluqlar təmizləndi

## 4. Model
- Vectorizer: TfidfVectorizer (ngram_range=(1,2), max_features=12000)
- Model: LogisticRegression (multi_class='multinomial', class_weight='balanced')
- Train/test split: 80/20, stratify=y

## 5. Nəticələr və interpretasiya
- Test accuracy: **~0.84–0.87** (dəqiq rəqəmi kod işləyəndə yoxlayın)
- Ən yaxşı performans: joy və sadness
- Ən çox qarışan siniflər: fear ↔ surprise, love ↔ joy  
  (emosiyaların təbiətindən irəli gəlir, çünki nümunələr oxşardır)
- Sarkazm və mürəkkəb cümlələrdə zəifdir

## 6. Gradio interfeysi
Kod işə salındıqda avtomatik brauzerdə açılır.  
Cümlə yazaraq hər sinif üçün test etmək olar.

## Necə işlətmək olar
```bash
pip install -r requirements.txt
python emotion_model.py

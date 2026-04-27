from sklearn.feature_extraction.text import CountVectorizer
from sklearn.naive_bayes import MultinomialNB

# Eğitim verisi
texts = [
    "bu film çok güzel",
    "harika bir deneyimdi",
    "çok kötüydü",
    "hiç beğenmedim",
    "mükemmel bir ürün",
    "rezalet bir hizmet",
]

# 1 = pozitif, 0 = negatif
labels = [1, 1, 0, 0, 1, 0]

# Metinleri sayısal veriye çevir
vectorizer = CountVectorizer()
X = vectorizer.fit_transform(texts)

# Model oluştur ve eğit
model = MultinomialNB()
model.fit(X, labels)

# Test
while True:
    user_input = input("Bir cümle yaz (çıkmak için q): ")
    if user_input.lower() == "q":
        break

    test = vectorizer.transform([user_input])
    prediction = model.predict(test)

    if prediction[0] == 1:
        print("Pozitif 🙂")
    else:
        print("Negatif 🙁")

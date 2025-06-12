# Crypto
crypto_db = {  
    "Bitcoin": {  
        "price_trend": "rising",  
        "market_cap": "high",  
        "energy_use": "high",  
        "sustainability_score": 3/10  
    },  
    "Ethereum": {  
        "price_trend": "stable",  
        "market_cap": "high",  
        "energy_use": "medium",  
        "sustainability_score": 6/10  
    },  
    "Cardano": {  
        "price_trend": "rising",  
        "market_cap": "medium",  
        "energy_use": "low",  
        "sustainability_score": 8/10  
    }  
}
def crypto_buddy(user_query):
    user_query = user_query.lower()

    if "sustainable" in user_query or "eco" in user_query:
        recommend = max(crypto_db, key=lambda x: crypto_db[x]["sustainability_score"])
        print(f"CryptoBuddy: Invest in {recommend}!  It’s eco-friendly and has long-term potential!")
    
    elif "trending up" in user_query or "rising" in user_query:
        trending_cryptos = [name for name, data in crypto_db.items() if data["price_trend"] == "rising"]
        print(f"CryptoBuddy: These coins are trending up : {', '.join(trending_cryptos)}")
    
    elif "long-term" in user_query or "growth" in user_query:
        for name, data in crypto_db.items():
            if data["price_trend"] == "rising" and data["sustainability_score"] > 0.7:
                print(f"CryptoBuddy: {name} is trending up and has a top-tier sustainability score! ")
                break
        else:
            print("CryptoBuddy: Consider balancing both growth and sustainability. No perfect match found.")
    
    elif "most profitable" in user_query or "best investment" in user_query:
        profitable = [
            name for name, data in crypto_db.items()
            if data["price_trend"] == "rising" and data["market_cap"] == "high"
        ]
        if profitable:
            print(f"CryptoBuddy: Based on market trends, you should check out: {', '.join(profitable)} ")
        else:
            print("CryptoBuddy: No high-market, rising coins at the moment.")

    else:
        print("CryptoBuddy: I didn’t quite get that . Try asking about sustainability, growth, or what's trending.")
# Simulate a few user queries
crypto_buddy("Which crypto is trending up?")
crypto_buddy("What’s the most sustainable coin?")
crypto_buddy("Which crypto should I buy for long-term growth?")
crypto_buddy("What's the most profitable investment right now?")
print("Crypto is risky—always do your own research! This is not financial advice.")

import re

# List of blocked words (you can grow this list)
blocked_keywords = [
    "nudity", "porn", "sex", "violence", "explicit", "gambling",
    "drugs", "profanity", "curse", "nsfw"
]

def is_safe_query(query):
    # Case insensitive keyword check
    query_lower = query.lower()
    for word in blocked_keywords:
        if re.search(r'\b' + re.escape(word) + r'\b', query_lower):
            return False
    return True

import re

def assess_password_strength(password):
    """Assess the strength of a given password and provide feedback."""
    
    # Define password strength criteria
    length_criteria = len(password) >= 8
    uppercase_criteria = bool(re.search(r'[A-Z]', password))
    lowercase_criteria = bool(re.search(r'[a-z]', password))
    number_criteria = bool(re.search(r'[0-9]', password))
    special_char_criteria = bool(re.search(r'[!@#$%^&*(),.?":{}|<>]', password))

    # Calculate strength score
    strength_score = sum([length_criteria, uppercase_criteria, lowercase_criteria, number_criteria, special_char_criteria])

    # Provide feedback based on strength score
    if strength_score == 5:
        return "✅ Strong Password: Your password is very secure!"
    elif strength_score == 4:
        return "🟢 Good Password: Consider adding more complexity."
    elif strength_score == 3:
        return "🟡 Medium Password: Use a mix of uppercase, numbers, and symbols."
    elif strength_score == 2:
        return "🔴 Weak Password: Increase length and add more character types."
    else:
        return "❌ Very Weak Password: Your password is too easy to guess!"

if __name__ == "__main__":
    user_password = input("password")
    feedback = assess_password_strength(user_password)
    print(feedback)

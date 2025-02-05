def factorial(n):
    """
    計算階層 n! 的結果
    使用迴圈方式來避免遞迴限制
    """
    if n < 0:
        raise ValueError("Factorial is not defined for negative numbers.")
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result

def factorial_division(a, b):
    """
    計算 a! / (b! * (a-b)!) 的結果
    確保輸入為數字，且分母不為零
    """
    # 檢查輸入是否為整數
    if not (isinstance(a, int) and isinstance(b, int)):
        raise TypeError("Inputs must be integers.")
    
    # 檢查分母是否為零
    if b > a:
        raise ValueError("The denominator factorial will be zero (b > a).")
    
    try:
        result = factorial(a) // (factorial(b) * factorial(a - b))
    except ZeroDivisionError:
        raise ZeroDivisionError("Division by zero occurred.")
    return result

def main():
    try:
        a = int(input("Enter the first number (a): "))
        b = int(input("Enter the second number (b): "))
        result = factorial_division(a, b)
        print(f"The result of {a}! / ({b}! * ({a}-{b})!) is: {result}")
    except Exception as e:
        print(f"Error: {e}")

if __name__ == "__main__":
    main()

"""
這個小程式展示了使用 Python 計算組合數的技巧，特別是使用迴圈來實作階層，
並加入基本的錯誤檢查（確保輸入為整數且分母不為零）。
"""

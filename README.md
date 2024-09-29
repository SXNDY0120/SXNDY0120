import sys

# Function to calculate the maximum profit Ratan can make
def calculate_max_profit(prices):
    """
    This function computes the maximum possible profit from a list of stock prices,
    where each element represents the stock price on a given day.
    
    Parameters:
    prices (List[int]): A list of integers representing stock prices on consecutive days.

    Returns:
    int: The maximum profit that can be made by buying and selling once.
    """
    
    # Initialize minimum price to a very large number and max_profit to 0
    min_price = sys.maxsize  # Represents positive infinity for min comparison
    max_profit = 0  # No transaction means zero profit initially

    # Iterate through each price in the prices array
    for price in prices:
        # Update the minimum price encountered up to the current day
        if price < min_price:
            min_price = price
        
        # Calculate the potential profit by selling at the current price
        profit = price - min_price
        
        # Update the maximum profit observed so far
        if profit > max_profit:
            max_profit = profit
    
    return max_profit

# Function to handle input/output operations
def main():
    """
    Main function to handle the input and output for the stock profit calculation.
    It reads from standard input and prints the maximum profit to standard output.
    """
    
    try:
        # Read the number of days
        n = int(input().strip())
        
        # Read the stock prices for 'n' days
        prices = list(map(int, input().strip().split()))

        # Check if the number of prices match the input count
        if len(prices) != n:
            raise ValueError("The number of prices does not match the provided 'n' value.")

        # Calculate and print the maximum profit
        result = calculate_max_profit(prices)
        print(result)
    
    except ValueError as e:
        print(f"Invalid input: {e}")
    except Exception as e:
        print(f"An error occurred: {e}")

# Entry point of the program
if _name_ == "_main_":
    main()

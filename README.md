# bcg-genai-financial-chatbot
Prototype of a rule-based AI financial chatbot developed during the BCG GenAI Job Simulation on Forage.
import pandas as pd
data = [
    ["Microsoft", 2022, 198.27, 72.74, 364.84, 198.30, 89.04],
    ["Microsoft", 2023, 211.92, 72.36, 411.98, 205.75, 87.58],
    ["Microsoft", 2024, 245.12, 88.14, 512.16, 243.69, 89.04],
    ["Tesla", 2021, 53.82, 5.53, 52.97, 30.55, 5.94],
    ["Tesla", 2022, 81.46, 12.76, 82.34, 36.44, 14.72],
    ["Tesla", 2023, 96.77, 15.00, 94.97, 36.44, 13.26],
    ["Apple", 2021, 365.82, 94.68, 351.00, 287.91, 104.04],
    ["Apple", 2022, 394.33, 99.80, 352.76, 302.08, 122.15],
    ["Apple", 2023, 382.99, 96.99, 383.29, 313.67, 110.54]
]

columns = ["Company","Fiscal Year","Total Revenue","Net Income","Total Assets","Total Liabilities","Operating Cash Flow"]
df = pd.DataFrame(data, columns=columns)
df['Revenue Growth (%)'] = df.groupby('Company')['Total Revenue'].pct_change()*100
df['Net Income Growth (%)'] = df.groupby('Company')['Net Income'].pct_change()*100## Key Insights
# Microsoft shows consistent growth driven by cloud revenue.
# Tesla shows strong revenue growth but volatile cash flows.
# Apple remains stable with strong operating cash generation.

#These trends are suitable for integration into an AI-powered financial chatbot.

def simple_chatbot():
    print("--- Financial Analysis Chatbot Prototype ---")
    print("Ask me about Microsoft, Tesla, or Apple's financials.")
    print("Type 'exit' to quit.\n")

    while True:
        user_input = input("User: ").strip().lower()

        if user_input == "exit":
            print("Chatbot: Goodbye!")
            break

        # Query 1: Microsoft Revenue 2024
        if "microsoft" in user_input and "revenue" in user_input and "2024" in user_input:
            response = "The total revenue for Microsoft in 2024 was $245.12 billion."
        
        # Query 2: Tesla Net Income 2023
        elif "tesla" in user_input and "net income" in user_input and "2023" in user_input:
            response = "Tesla's net income in 2023 was $15.00 billion."
        
        # Query 3: Apple Revenue Change
        elif "apple" in user_input and "revenue" in user_input and "change" in user_input:
            response = "Apple's revenue decreased by $11.34 billion from 2022 ($394.33B) to 2023 ($382.99B)."
        
        # Query 4: Microsoft Assets 2023
        elif "microsoft" in user_input and "assets" in user_input and "2023" in user_input:
            response = "Microsoft's total assets for 2023 were $411.98 billion."
            
        # Query 5: Highest Cash Flow 2022
        elif "highest" in user_input and "cash flow" in user_input and "2022" in user_input:
            response = "Apple had the highest operating cash flow in 2022 at $122.15 billion."

        else:
            response = "I'm sorry, I can only provide information on predefined queries regarding 2021-2024 fiscal data for Microsoft, Tesla, and Apple."

        print(f"Chatbot: {response}\n")

if __name__ == "__main__":
    simple_chatbot()

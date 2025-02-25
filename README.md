## Language
- [English](README.md)
- [中文](README_zh.md)

---

## **Project Introduction**

AutoDCF is a stock valuation tool based on the Discounted Cash Flow (DCF) model. By analyzing a company's historical financial data, it provides core variable references for future cash flow projections and automatically calculates the intrinsic value of the company based on user-input valuation parameters.

Automating the process of data collection and valuation calculation significantly saves time on data organization and processing, helping investors quickly evaluate the intrinsic value of stocks and assist in investment decision-making.

---

## **Project Highlights**

- **Automation**: By inputting the stock code, the system automatically retrieves the company’s historical data from a financial data API, supporting customized historical periods and lengths. After entering key valuation parameters, the system automatically calculates future cash flow projections and the intrinsic value of the company.
- **Interactivity**: From displaying historical financial data, entering valuation parameters, to the final valuation results and sensitivity analysis, all steps are clearly presented in the terminal for easy understanding.
- **Excel Export**: Supports exporting the valuation results to an Excel file, making it easy for archiving and further analysis or adjustments.

---

## **The Importance of DCF Valuation in Value Investing**

Discounted Cash Flow (DCF) valuation, which reflects a company’s intrinsic value, is a key tool in value investing. Price is what we pay, value is what we get. No matter how good a company is, if bought at too high a price, it loses its investment value. As Buffett said, forget buying fair businesses at wonderful prices; instead, buy wonderful businesses at fair prices. DCF valuation is the critical tool to help us determine that “fair price” or intrinsic value.

DCF valuation involves several assumptions, and this project aims to minimize the manual input of parameters, focusing on three core variables: revenue growth, operating efficiency (EBIT margin), and reinvestment, offering a "vaguely correct" framework. As Buffett said, "I would rather be vaguely right than precisely wrong." Through fuzzy valuation, we can better understand the key drivers behind stock valuations and use sensitivity analysis to find the margin of safety. In a stock market full of uncertainties, DCF valuation offers us a clear path to long-term success.

---

## **Installation and Usage**

### **1. Download the Project**

### **Method 1: Clone the Project Using Git**

1. Open your terminal and run the following command to clone the project locally:
    
    ```
    git clone <https://github.com/alanhewenyu/AutoDCF.git>
    
    ```
    
2. Enter the project directory:
    
    ```
    cd AutoDCF
    
    ```
    

### **Method 2: Download the ZIP File**

1. Click the **Code** button at the top right of the page and select **Download ZIP**.
2. Extract the downloaded ZIP file to your computer.

---

### **2. Install Dependencies**

1. Ensure that Python 3.8 or higher is installed. You can check the Python version with the following command:
    
    ```
    python --version
    
    ```
    
    If Python is not installed, visit the [official Python website](https://www.python.org/downloads/) to download and install it.
    
2. Install the required dependencies for the project:
    - Open the terminal and navigate to the project directory (if you downloaded the ZIP file, navigate to the extracted folder).
    - Run the following command to install the dependencies:
        
        ```
        pip install -r requirements.txt
        
        ```
        

---

### **3. Obtain an API Key**

This project uses financial data provided by [Financial Modeling Prep (FMP)](https://financialmodelingprep.com/). You need to register for an FMP account and obtain an API key.

FMP is a US-based financial data provider covering historical financial statements, market data, and valuation metrics for global listed companies. Compared to expensive financial terminals (such as Wind and Bloomberg), FMP offers a more lightweight service focused on stock data, covering a broad range of markets (like China A-shares, Hong Kong stocks, and US stocks). For retail investors, FMP provides comprehensive data at a more affordable price. If you need to pull historical financial data for globally listed companies and calculate DCF valuations via API, FMP is an ideal choice.

### **How to Set the API Key**

- **Method 1: Environment Variable**
    
    Set the API key as an environment variable:
    
    ```
    export FMP_API_KEY='your_api_key_here'
    
    ```
    
- **Method 2: Direct Code Modification**
    
    In the `main.py` file, find the default value for `args.apikey` and replace it with your API key.
    

---

### **4. Run the Program**

Open the terminal and navigate to the project directory. Run the following command to start the program:

```

python main.py
```

---

### **5. Usage Steps**

1. **Input Stock Code**: For example, `AAPL` (Apple Inc.).
2. **Select Financial Data Period**: Choose either annual (`annual`) or quarterly (`quarter`) data.
3. **View Historical Financial Data**: The program will display a summary of the company’s historical financial data.
4. **Input Key Valuation Parameters**:
    - **Revenue Growth Rate**: The growth rate for the next 1 year and 2-5 years.
    - **EBIT Margin**: The target EBIT margin.
    - **Convergence Years**: The number of years it will take to reach the target EBIT margin.
    - **Revenue-to-Invested Capital Ratio**: The ratio for different periods.
    - **Tax Rate**: The program will automatically calculate the average tax rate based on historical data, but you can adjust it manually.
    - **WACC**: The program will automatically calculate the Weighted Average Cost of Capital based on retrieved data, but it can also be manually adjusted.
5. **View Valuation Results**: The program will calculate the company’s intrinsic value and display the calculation process and final per-share price.
6. **Sensitivity Analysis**: The program will generate a sensitivity analysis table showing the impact of revenue growth rate and EBIT margin on the per-share price.
7. **Export Results**: Supports exporting the valuation results to an Excel file for further analysis and archiving.

### **Input Format Guidelines**

- Parameters that require percentage values (including revenue growth, EBIT margin, tax rate, and WACC) should be entered as numbers without the percentage sign. For example, if the revenue growth rate is 10%, simply enter `10` (not `10%`).
- The program will automatically interpret these numeric inputs as percentages (e.g., entering `10` will be interpreted as 10%).

---

## **Key Valuation Parameters Explanation**

| **Parameter Name** | **Description** |
| --- | --- |
| **Revenue Growth Rate (Year 1)** | The first-year revenue forecast, as companies typically provide guidance on their next year's performance. |
| **Revenue Growth Rate (Years 2-5)** | Compound annual growth rate (CAGR) for the next 2-5 years. |
| **EBIT Margin** | The EBIT margin the company is expected to reach once it matures and stabilizes. |
| **Convergence Years** | The number of years it will take for the company to reach the target EBIT margin. |
| **Revenue-to-Invested Capital Ratio (Year 1)** | You can refer to the historical revenue-to-invested capital ratio from the company’s historical financial data. However, note that historical data reflects past performance, and this ratio should consider the capital required for additional revenue. A good method is to also adjust the ratio by considering total reinvestment amounts from the historical financial data. |
| **Revenue-to-Invested Capital Ratio (Years 3-5)** | Same as above. |
| **Revenue-to-Invested Capital Ratio (Years 5-10)** | Same as above. |
| **Tax Rate** | The program will automatically calculate the company’s average tax rate over the historical period, which can be used directly or adjusted manually. |
| **WACC** | The program will automatically calculate the WACC based on risk-free rates, equity premium, and the company’s Beta value for the country. This can be used directly or adjusted manually. 
| **RONIC** | Economic theory suggests competition will eliminate abnormal returns, meaning companies in competitive industries will see long-term return on new invested capital (RONIC) equal to WACC. However, firms with sustainable competitive advantages (such as a strong brand) may maintain excess returns beyond 10 years.  In such cases, a higher RONIC than WACC can be used for terminal value calculation, with this valuation model’s preset value being WACC plus 5%. |

---

## **Contributions and Feedback**

If you have any suggestions or encounter issues, feel free to submit an Issue or Pull Request. You can also contact me via email: [alanhe@icloud.com](mailto:alanhe@icloud.com).

For more content on company valuation, follow my WeChat official account: **见山笔记**.

---

## **License**

This project is open-sourced under the MIT License. For more details, please refer to the [LICENSE](https://chat.deepseek.com/a/chat/s/LICENSE) file.
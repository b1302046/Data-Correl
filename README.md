import pandas as pd
from scipy import stats

df = pd.read_excel('Data_Correl.xlsx')

obesity = df['Obesity rate %']
internet_access = df['Access to internet per 100']

clean_data = df[['Obesity rate %', 'Access to internet per 100']].dropna()
obesity_clean = clean_data['Obesity rate %']
internet_clean = clean_data['Access to internet per 100']

r_value, p_value = stats.pearsonr(obesity_clean, internet_clean)

n = len(clean_data)
t_statistic = r_value * ((n - 2) ** 0.5) / ((1 - r_value ** 2) ** 0.5)

print(f"Correlation coefficient (r): {r_value:.4f}")
print(f"T-statistic: {t_statistic:.4f}")
print(f"P-value: {p_value:.4e}")
plt.show()

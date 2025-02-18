mport numpy as np
import matplotlib.pyplot as plt

# Parâmetros
S0 = 40       # Preço inicial
mu = 0.12      # Taxa de crescimento
sigma = 0.10   # Volatilidade
T = 1          # Tempo total (1 ano)
N = 254        # Número de passos (dias úteis)
M = 5         # Número de trajetórias
dt = T / N     # Intervalo de tempo

# Simulação das trajetórias
np.random.seed(42)  # Para reproducibilidade
trajetorias = np.zeros((M, N+1))
trajetorias[:, 0] = S0

for k in range(M):
    for n in range(N):
        epsilon = np.random.choice([1, -1])  # Cara ou coroa
        trajetorias[k, n+1] = trajetorias[k, n] + mu * trajetorias[k, n] * dt + \
                              sigma * trajetorias[k, n] * epsilon * np.sqrt(dt)

# Cálculo da média das trajetórias
media_trajetorias = np.mean(trajetorias, axis=0)

# Plotagem
plt.figure(figsize=(10, 6))
for k in range(M):
    plt.plot(trajetorias[k], color='green', alpha=0.5, linewidth=1)

plt.plot(media_trajetorias, color='red', linewidth=2, label='Média das 5 trajetórias')
plt.title('Simulação de Monte Carlo com ε = Cara ou Coroa')
plt.xlabel('Passos de Tempo')
plt.ylabel('Preço do Ativo (S)')
plt.legend()
plt.grid(True)
plt.show()

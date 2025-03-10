*Oie!* 👋
Aqui é a Maria Denardi! 💖

#6CPM - Pato Branco 🎖
#Turma de Exatas 📊
#Aviação ✈
#3ano 🏆

from PIL import Image, ImageDraw
import random

# Configuração do GIF
largura, altura = 64, 64  # Resolução pixelada
frames = []
num_frames = 10

def desenhar_praia(draw):
    """Desenha o cenário da praia."""
    # Céu
    draw.rectangle([0, 0, largura, altura // 2], fill=(135, 206, 250))  # Azul-claro
    
    # Mar (variação para criar ondas)
    for i in range(altura // 2, int(altura * 0.75), 3):
        cor_mar = (0, 105 + random.randint(-10, 10), 148)  # Azul-marinho variável
        draw.rectangle([0, i, largura, i + 3], fill=cor_mar)
    
    # Areia
    draw.rectangle([0, int(altura * 0.75), largura, altura], fill=(237, 201, 175))  # Bege-areia

for i in range(num_frames):
    img = Image.new("RGB", (largura, altura), "white")
    draw = ImageDraw.Draw(img)
    
    desenhar_praia(draw)
    
    # Pequenas alterações para dar a sensação de movimento
    if i % 2 == 0:
        draw.rectangle([0, altura // 2, largura, altura // 2 + 3], fill=(0, 115, 158))  # Onda mais escura
    
    frames.append(img)

# Salvar como GIF animado
frames[0].save("praia_pixelada.gif", save_all=True, append_images=frames[1:], duration=100, loop=0)

print("GIF criado: praia_pixelada.gif")

```html name=index.html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vendas de Brainrot - O Mercado do Conteúdo Surreal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f8f9fa;
        }
        .btn-add-to-cart {
            background-color: #ff6b35;
            color: white;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
        }
        .btn-add-to-cart:hover {
            background-color: #e55a2b;
        }
        .cart-item {
            border: 1px solid #ddd;
            padding: 10px;
            margin: 5px 0;
        }
    </style>
</head>
<body class="text-gray-800">
    <header class="bg-purple-600 text-white p-4">
        <nav class="flex justify-between items-center">
            <h1 class="text-2xl font-bold">Brainrot Emporium</h1>
            <ul class="flex space-x-4">
                <li><a href="#products" class="hover:underline">Produtos</a></li>
                <li><a href="#cart" class="hover:underline">Carrinho</a></li>
                <li><a href="#about" class="hover:underline">Sobre</a></li>
            </ul>
        </nav>
    </header>

    <section id="hero" class="text-center py-16 bg-gradient-to-r from-pink-400 to-purple-500 text-white">
        <h2 class="text-4xl font-bold mb-4">Bem-vindo ao Brainrot Emporium!</h2>
        <p class="text-lg">Vendas de produtos inspirados no caos do conteúdo viral. Desfaça sua mente com estilo!</p>
        <div class="mt-8">
            <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/375a5426-ac2b-4ca5-8bd3-d4504b3303b3.png" alt="Ilustração colorida de um cérebro estilizado sendo corroído por ícones de conteúdo viral, incluindo TikTok, memes e GIFs animados, em um fundo surreal com tons neon e efeitos distorcidos." class="mx-auto rounded-lg shadow-lg" />
        </div>
    </section>

    <section id="products" class="py-16 px-4 max-w-6xl mx-auto">
        <h3 class="text-3xl font-bold mb-8 text-center">Nossos Produtos Brainrot</h3>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <div class="bg-white p-6 rounded-lg shadow-md text-center">
                <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/824c1867-2dad-4a8c-a723-6b7a6ddf8274.png" alt="Representação gráfica de um hambúrguer achatado com emoji digitalizados derretendo, simbolizando um Brainrot Burger coberto em molho pixelado e itens memes." class="w-full h-48 object-cover rounded mb-4" />
                <h4 class="text-xl font-semibold">Brainrot Burger</h4>
                <p class="text-gray-600 mb-4">Um hambúrguer que leva sua mente a um estado de confusão viral. R$ 29,99</p>
                <button class="btn-add-to-cart" onclick="addToCart('Brainrot Burger', 29.99)">Adicionar ao Carrinho</button>
            </div>
            <div class="bg-white p-6 rounded-lg shadow-md text-center">
                <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/8a26d3cf-4373-4d56-a2ca-3512df405455.png" alt="Ilustração abstrata de uma dança viral com figuras pixeladas em movimentos frenéticos, combos de break dance e saltos impossíveis em um palco holográfico brilhante." class="w-full h-48 object-cover rounded mb-4" />
                <h4 class="text-xl font-semibold">Viral Dance Pack</h4>
                <p class="text-gray-600 mb-4">Pacote de passos de dança que sabotam sua coordenação. R$ 49,99</p>
                <button class="btn-add-to-cart" onclick="addToCart('Viral Dance Pack', 49.99)">Adicionar ao Carrinho</button>
            </div>
            <div class="bg-white p-6 rounded-lg shadow-md text-center">
                <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/609ec5af-3028-4924-9811-ebd3009a8a47.png" alt="Imagem surreal de uma xícara de café digital com vapor pixelado subindo, rodeada de pensamentos caóticos representados por nuvens deformadas e ícones de notificação piscando." class="w-full h-48 object-cover rounded mb-4" />
                <h4 class="text-xl font-semibold">Café da Distração</h4>
                <p class="text-gray-600 mb-4">Copo de café que acelera sua rolagem infinita. R$ 19,99</p>
                <button class="btn-add-to-cart" onclick="addToCart('Café da Distração', 19.99)">Adicionar ao Carrinho</button>
            </div>
        </div>
    </section>

    <section id="cart" class="py-16 px-4 max-w-6xl mx-auto bg-white rounded-lg shadow-md">
        <h3 class="text-3xl font-bold mb-8 text-center">Carrinho de Compras</h3>
        <div id="cart-items"></div>
        <p id="cart-total" class="text-xl font-semibold mt-4">Total: R$ 0,00</p>
        <button class="bg-green-500 text-white py-2 px-4 rounded mt-4 hover:bg-green-600">Finalizar Compra</button>
    </section>

    <footer id="about" class="bg-gray-800 text-white py-8 text-center">
        <p>© 2023 Brainrot Emporium. Todos os direitos reservados à ilusão digital.</p>
        <p>Contato surreal: brainrot@chaos.com | Siga-nos no @BrainrotEmporium (fictício).</p>
    </footer>

    <script>
        let cart = [];

        function addToCart(name, price) {
            cart.push({ name, price });
            updateCart();
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            updateCart();
        }

        function updateCart() {
            const cartItemsDiv = document.getElementById('cart-items');
            cartItemsDiv.innerHTML = '';
            let total = 0;
            cart.forEach((item, index) => {
                total += item.price;
                cartItemsDiv.innerHTML += `
                    <div class="cart-item flex justify-between items-center">
                        <span>${item.name} - R$ ${item.price.toFixed(2)}</span>
                        <button onclick="removeFromCart(${index})" class="text-red-500">Remover</button>
                    </div>
                `;
            });
            document.getElementById('cart-total').textContent = `Total: R$ ${total.toFixed(2)}`;
        }
    </script>
</body>
</html>
```

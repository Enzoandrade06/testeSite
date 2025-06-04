document.querySelectorAll('.menu a').forEach(link => {
  link.addEventListener('click', () => {
    document.querySelector('.menu-wrapper').classList.remove('active');
  });
});

document.addEventListener('DOMContentLoaded', () => {
    console.log("Documento carregado. Iniciando accordion...");

    document.querySelectorAll(".accordion-toggle").forEach(button => {
        const icon = document.createElement('span');
        icon.classList.add('accordion-icon');
        icon.textContent = '+';
        button.appendChild(icon);

        button.addEventListener('click', function(e) {
            e.preventDefault();
            console.log(`Botão clicado: ${button.textContent.trim()}`);

            button.classList.toggle('active');
            const content = button.nextElementSibling;

            if (content) {
                content.classList.toggle('active');

                if (content.classList.contains('active')) {
                    icon.textContent = '-';
                    icon.style.transform = 'translateY(-50%) rotate(90deg)';
                    console.log("Conteúdo EXPANDIDO.");
                } else {
                    icon.textContent = '+';
                    icon.style.transform = 'translateY(-50%) rotate(0deg)';
                    console.log("Conteúdo RECOLHIDO.");
                }
            } else {
                console.warn("Nenhum conteúdo encontrado após este botão.");
            }
        });
    });
});
document.addEventListener('DOMContentLoaded', () => {
    console.log("Carrossel Painel Ripado iniciado...");
    initCarrossel('.carrossel-painel-ripado');

    console.log("Carrossel Painel Instalado...");
    initCarrossel('.carrossel-instalacoes-ripado');

    console.log("Carrossel Galeria Primeclick iniciado...");
    initCarrossel('.carrossel-galeria-primeclick');
});

document.addEventListener('DOMContentLoaded', () => {
  document.querySelectorAll('.carrossel-painel-ripado, .carossel-instalacoes-ripado .carrossel-galeria-primeclick').forEach(carrossel => {
    const slideContainer = carrossel.querySelector('.slide-container');
    const produtos = slideContainer.querySelectorAll('.produto');
    const dotsContainer = carrossel.querySelector('.dots');
    const prevBtn = carrossel.querySelector('.prev');
    const nextBtn = carrossel.querySelector('.next');

    const itemsPerPage = 3;
    const totalSlides = Math.ceil(produtos.length / itemsPerPage);
    let current = 0;
    let intervalId;

    const criarBolinhas = () => {
      dotsContainer.innerHTML = '';
      Array.from({ length: totalSlides }, (_, i) => {
        const dot = document.createElement('span');
        dot.className = 'dot' + (i === 0 ? ' active' : '');
        dot.addEventListener('click', () => {
          current = i;
          showSlide();
          resetInterval();
        });
        dotsContainer.appendChild(dot);
      });
    };

    const showSlide = () => {
      const offset = produtos[0].offsetWidth * itemsPerPage * current;
      slideContainer.style.transform = `translateX(-${offset}px)`;
      slideContainer.style.transition = 'transform 0.5s ease';

      dotsContainer.querySelectorAll('.dot').forEach((dot, i) => {
        dot.classList.toggle('active', i === current);
      });
    };

    const changeSlide = dir => {
      current = (current + dir + totalSlides) % totalSlides;
      showSlide();
    };

    const resetInterval = () => {
      clearInterval(intervalId);
      intervalId = setInterval(() => changeSlide(1), 5000);
    };

    prevBtn.addEventListener('click', () => {
      changeSlide(-1);
      resetInterval();
    });

    nextBtn.addEventListener('click', () => {
      changeSlide(1);
      resetInterval();
    });

    window.addEventListener('resize', showSlide);

    criarBolinhas();
    showSlide();
    resetInterval();
  });
});

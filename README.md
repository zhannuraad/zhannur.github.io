<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Movies and Genres</title>
    <link rel="stylesheet" href="style.css"> 
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tooltipster@4.2.8/dist/css/tooltipster.bundle.min.css">
    <style>
       
        table {
            width: 100%;
            border-collapse: collapse;
        }

        table, th, td {
            border: 1px solid rgb(171, 102, 102);
        }

        th, td {
            padding: 8px;
            text-align: left;
        }

        th {
            cursor: pointer;
        }

        
        #filters {
            margin-bottom: 20px;
        }
    </style>

   <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  
   <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>

   <script src="https://cdn.jsdelivr.net/npm/tooltipster@4.2.8/dist/js/tooltipster.bundle.min.js"></script>

</head>
<body>
    
<header>
    <h1>Movies and Genres</h1>
</header>

<main>
    <div class="styled-text">
        <center><p>Добро пожаловать в мир кино!</p></center>
    </div>
    <h2>Популярные фильмы</h2>
    
    <div class="image-text-container">
       <table class="tabb">
            <tr><td>
            <img class="ima" src="https://avatars.mds.yandex.net/i?id=4def263327147217ba5d99e6b67e9d98192e90a6-4032453-images-thumbs&n=13" width="850" alt="Популярные фильмы" />
            <p>Фи́льм (перевод с английского языка слова film означает плёнка) — кинопроизведение или совокупность фотографических кадров (изображений), которые последовательно расположены на фотоплёнке. Кадры предназначены для просмотра на экране и связаны одним сюжетом. Фильмы создаются в киностудиях группами технических специалистов и творческих людей. При создании киноленты применяются различные технические и компьютерные средства. Фильмы снимаются в специальных павильонах и на реальных площадках (города и природные объекты)</p>
            </td></tr>
        </table>
   </div>
  


    <table  class="tab" border="1">
        <thead>
            <tr>
                <th onclick="sortTable(0)">Название</th>
                <th onclick="sortTable(1)">Жанр</th>
                <th onclick="sortTable(2)">Год</th>
            </tr>
        </thead>
        <tbody>
          
            <tr>
                <td><a href="https://rezka.ag/films/melodrama/30604-posle-2019.html" target="_blank">После</a></td>
                <td>Мелодрама</td>
                <td>2010</td>
            </tr>
            <tr>
                <td><a href="https://rezka.ag/films/comedy/833-odin-doma-1990.html" target="_blank">Один дома</a></td>
                <td>Комедия</td>
                <td>1972</td>
            </tr>
            <tr>
                <td><a href="https://rezka.ag/films/action/1031-posledniy-samuray-2003.html" target="_blank">Паразиты</a></td>
                <td>Ужастик</td>
                <td>2019</td>
            </tr>
            <tr>
                <td><a href="https://rezka.ag/films/action/1031-posledniy-samuray-2003.html" target="_blank">Последний самурай</a></td>
                <td>Боевик</td>
                <td>2003</td>
            </tr>
            <tr>    
                <td><a href="https://rezka.ag/films/fantasy/1043-garri-potter-i-filosofskiy-kamen-2001.html" target="_blank">Гарри Потер</a></td>
                <td>Фантастический</td>
                <td>2001</td>
            </tr>
            <tr> 
                <td><a href="https://www.kinopoisk.ru/film/17914/?utm_referrer=yandex.kz" target="_blank">Клеопатра</a></td>
                <td>Исторический</td>
                <td>1963</td>
            </tr>
        </tbody>
        
    </table>
    
    <button id="sortByYear" onclick="sortTable(2)">Сортировать по Году</button>
    <h2>Жанры кино</h2>
    <ul>
        <li>Комедия</li>
        <li>Мелодрама</li>
        <li>Ужастик</li>
        <li>Боевик</li>
        <li>Фантастический </li>
        <li>Исторический</li>
    </ul>

    
    <h2>Предложить фильм</h2>
     <div id="app">
        <form @submit.prevent="addFilm">
        <div>
            <label for="title">Название</label>
            <input type="text" v-model="newFilm.title" required>
        </div>
        <div>
            <label for="genre">Жанры:</label>
            <select id="genre" name="genre">
                <option value="комедия">Комедия</option>
                <option value="ужастик">Ужастик</option>
                <option value="мелодрама">Мелодрама</option>
                <option value="боевик">Боевик</option>
                <option value="фантастический">Фантастический</option>
                <option value="исторический">Исторический</option>
            </select>
        </div>
        
        <div>
            <label for="year">Год</label>
            <input type="number" v-model="newFilm.year" min="1950" max="2024" required>
        </div>
        <div>
            <label for="comments">Комментарий</label>
            <textarea id="comments" name="comments" rows="4"></textarea>
        </div>
        <div>
            <button type="submit">Добавить фильм</button>
        </div>
    </form>

    <h3>Список предложенных фильмов</h3>
    <table>
        <thead>
            <tr>
                <th>Название</th>
                <th>Жанр</th>
                <th>Год</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="film in films" :key="film.title">
                <td>{{ film.title }}</td>
                <td>{{ film.genre }}</td>
                <td>{{ film.year }}</td>
            </tr>
        </tbody>
    </table>
 <button @click="toggleInfo">{{ showInfo ? 'Скрыть' : 'Показать' }} информацию</button>
 <div v-show ="showInfo">
     <p> Фильм — отдельное произведение киноискусства. 14 В технологическом плане это последовательность движущихся изображений (кадров), связанных единым сюжетом. </p>
 </div>
 <button class="tooltip" title="Нажмите, чтобы узнать больше о фильмах" onclick="showScreenInfo()">Информация о экране</button>
</div>
<h1>Фильмы</h1>


<div id="filters">
    <label for="genreFilter">Фильтр по жанру:</label>
    <select id="genreFilter">
        <option value="">Все</option>
        <option value="Мелодрама">Детектив</option>
        <option value="Комедия">Драма</option>
        <option value="Ужастик">Триллер</option>
        <option value="Боевик">Мелодрама</option>
        <option value="Фантастический">Научная фантастика</option>
        <option value="Исторический">Романтика</option>
        <option value="Исторический">Приключения</option>
    </select>

    <label for="yearFilter">Фильтр по году:</label>
    <input type="number" id="yearFilter" placeholder="Введите год" min="1900" max="2024">
</div>
<table id="moviesTable">
    <thead>
        <tr>
            <th onclick="sortTable(0)">Название</th>
            <th onclick="sortTable(1)">Жанр</th>
            <th onclick="sortTable(2)">Год</th>
        </tr>
    </thead>
    <tbody>
        
    </tbody>
</table>

<button id="sortByTitle" onclick="sortTable(0)">Сортировать по Названию</button>
<button id="sortByGenre" onclick="sortTable(1)">Сортировать по Жанру</button>
<button id="sortByYear" onclick="sortTable(2)">Сортировать по Году</button>

</main>

<script>

function sortTable(n) {
    const table = document.querySelector(".tab tbody");
    const rows = Array.from(table.rows);
    const dir = table.dataset.sortDir === 'asc' ? 'desc' : 'asc';


   
    $(table).fadeOut(300, function() {
        rows.sort((a, b) => {
            const x = a.cells[n].innerText;
            const y = b.cells[n].innerText;

            if (n === 2) {
                return dir === 'asc' ? x - y : y - x;
            } else {
                return x.localeCompare(y);
            }
        });

    rows.forEach(row => table.appendChild(row));
    table.dataset.sortDir = dir;
     
     $(table).fadeIn(300);
})
}


$(document).ready(function() {
    $('#sortByYear').click(function() {
        $('td').css('color', 'blue');
        $('table').toggleClass('highlight');
    });
    
    
    $("table").tablesorter();

   
    var films = [
        "После", "Один дома", "Паразиты", "Последний самурай", "Гарри Потер", "Клеопатра"
    ];

    $("#titleInput").autocomplete({
        source: films
    });
});


new Vue({
    el: '#app',
    data: {
        newFilm: {
            title: '',
            genre: '',
            year: '',
        },
        films: [],
        showInfo: false
    },
    methods: {
        addFilm() {
            this.films.push({ ...this.newFilm });
            this.newFilm.title = '';
            this.newFilm.genre = '';
            this.newFilm.year = '';
              
    const newRow = $('<tr><td>' + this.newFilm.title + '</td><td>' + this.newFilm.genre + '</td><td>' + this.newFilm.year + '</td></tr>');
        },
        toggleInfo() {
            this.showInfo = !this.showInfo;
        },
        showScreenInfo() {
            alert("На экране отображается информация о фильмах!");
        }
    }
});

$(document).ready(function() {
    $('.tooltip').tooltipster({
        theme: 'tooltipster-light',
        trigger: 'hover'
    });
});       
</script>
<script>
    
    function loadXMLData() {
        const xhr = new XMLHttpRequest();
        xhr.open('GET', 'movies.xml', true); 
        xhr.onload = function() {
            if (xhr.status === 200) {
                const xml = xhr.responseXML;
                displayMovies(xml);
            }
        };
        xhr.send();
    }
    
    
    function displayMovies(xml) {
        const moviesTableBody = document.querySelector('#moviesTable tbody');
        const movies = xml.getElementsByTagName('movie');
        
        
        moviesTableBody.innerHTML = '';
    
      
        Array.from(movies).forEach(function(movie) {
            const title = movie.getElementsByTagName('title')[0].textContent;
            const genre = movie.getElementsByTagName('genre')[0].textContent;
            const year = movie.getElementsByTagName('year')[0].textContent;
    
            const row = document.createElement('tr');
            row.innerHTML = `<td>${title}</td><td>${genre}</td><td>${year}</td>`;
            moviesTableBody.appendChild(row);
        });
    }
    
    function sortTable(n) {
        const table = document.getElementById('moviesTable');
        const rows = Array.from(table.rows).slice(1); 
    
        rows.sort((a, b) => {
            const cellA = a.cells[n].textContent.trim();
            const cellB = b.cells[n].textContent.trim();
            
            if (n === 2) { 
                return parseInt(cellA) - parseInt(cellB);
            } else { 
                return cellA.localeCompare(cellB);
            }
        });
    
       
        rows.forEach(row => table.appendChild(row));
    }
    
   
    function filterMovies() {
        const genreFilter = document.getElementById('genreFilter').value.toLowerCase();
        const yearFilter = document.getElementById('yearFilter').value;
        
        const rows = document.querySelectorAll('#moviesTable tbody tr');
        rows.forEach(row => {
            const genre = row.cells[1].textContent.toLowerCase();
            const year = row.cells[2].textContent;
            
            
            const genreMatch = !genreFilter || genre.includes(genreFilter);
            const yearMatch = !yearFilter || year.includes(yearFilter);
            
            if (genreMatch && yearMatch) {
                row.style.display = '';
            } else {
                row.style.display = 'none';
            }
        });
    }
    
    
    document.getElementById('genreFilter').addEventListener('change', filterMovies);ғ
    document.getElementById('yearFilter').addEventListener('input', filterMovies);
    
  
    window.onload = function() {
        loadXMLData();
    };
    </script>
</body>
</html>
<?xml version="1.0" encoding="UTF-8"?>
<movies>
    <movie>
        <title>Гарри Поттер и философский камень</title>
        <genre>Фэнтези</genre>
        <year>2001</year>
    </movie>
    <movie>
        <title>Гарри Поттер и тайная комната</title>
        <genre>Приключения</genre>
        <year>2002</year>
    </movie>
    <movie>
        <title>Гарри Поттер и узник Азкабана</title>
        <genre>Фэнтези</genre>
        <year>2004</year>
    </movie>
    <movie>
        <title>Гарри Поттер и кубок огня</title>
        <genre>Фэнтези</genre>
        <year>2005</year>
    </movie>
    <movie>
        <title>Гарри Поттер и орден Феникса</title>
        <genre>Фэнтези</genre>
        <year>2007</year>
    </movie>
    <movie>
        <title>Гарри Поттер и принц-полукровка</title>
        <genre>Мелодрама</genre>
        <year>2009</year>
    </movie>
    <movie>
        <title>Гарри Поттер и дари смерти: Часть 1</title>
        <genre>Драма</genre>
        <year>2010</year>
    </movie>
    <movie>
        <title>Гарри Поттер и дари смерти: Часть 2</title>
        <genre>Драма</genre>
        <year>2011</year>
    </movie>
    <movie>
        <title>Шерлок Холмс</title>
        <genre>Детектив</genre>
        <year>2009</year>
    </movie>
    <movie>
        <title>Шерлок Холмс: Игра теней</title>
        <genre>Детектив</genre>
        <year>2011</year>
    </movie>
    <movie>
        <title>Зодиак</title>
        <genre>Триллер</genre>
        <year>2007</year>
    </movie>
    <movie>
        <title>Исчезнувшая</title>
        <genre>Триллер</genre>
        <year>2014</year>
    </movie>
    <movie>
        <title>Убийство на улице Морг</title>
        <genre>Мистика</genre>
        <year>2006</year>
    </movie>
    <movie>
        <title>Пятый элемент</title>
        <genre>Научная фантастика</genre>
        <year>1997</year>
    </movie>
    <movie>
        <title>Интерстеллар</title>
        <genre>Научная фантастика</genre>
        <year>2014</year>
    </movie>
    <movie>
        <title>Титаник</title>
        <genre>Романтика</genre>
        <year>1997</year>
    </movie>
    <movie>
        <title>500 дней лета</title>
        <genre>Романтика</genre>
        <year>2009</year>
    </movie>
    <movie>
        <title>Темные начала</title>
        <genre>Приключения</genre>
        <year>2007</year>
    </movie>
</movies>


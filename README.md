# -GDS-Challenge-submission
the readme for the Gov.UK inversity challenge
18/12/24 used figma to make a simple search icon and make a wireframe for the page(later scrapped)
19/12/24 and up to the beginning of the christmas holiday i was doing market research. this involved looking at and using the Gov.UK website and seeing what issues or irritations appeared. most of the large articles took a long time to read through and the information in them varied a lot covering a broad spectrum which is good unless you have to find one specific thing. that's why i decided to make an additional searchbar for every page; it would be a small circular search icon that when pressed on would expand into a searchbar that the user could use to search that page for specific words or phrases
2/1/25 downloaded the figma app and made some changes to the magnifying glass icon. Made it a more professional design by using a pre-made icon(unfortunately it wasn't added into the website page)
6/1/25 Found out how to make a website with code and the notepad html. Used ChatGPT to make base for main page.
7/1/25 Made some major design improvements and most of the main components of the main page were complete, links to gov.uk pages and a searchbar.
8/1/25 ChatGPT struggled to improve the code much further whenever i tried to get it to edit something it removed a lot of code. Planned to have a functioning sidebar menu that would drop in and out, because of the loss of major components i took an older version of website to submit with less of the design improvements; this also meant that the main feature i added(the page specific search to not function correctly unfortunately)
     ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                                                                                                                                       The actual code because i can't import it for some reason                                                                                                             <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GOV.UK Clone</title>

    <style>
        /* Basic Styles */
        body {
            font-family: 'Public Sans', sans-serif;
            line-height: 1.6;
            background-color: #555555; /* Darker grey background */
            color: white;
            margin: 0;
        }

        h1, h2 {
            background-color: #17203D; /* Dark blue */
            color: white;
            padding: 10px;
            margin-top: 0;
            border-radius: 4px;
        }

        /* Article card style */
        .govuk-card {
            border: 1px solid #444444; /* Darker grey border */
            padding: 20px;
            background-color: #444444; /* Dark grey box background */
            margin-bottom: 20px;
            border-radius: 6px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2); /* Subtle shadow */
        }

        .govuk-card__content {
            padding: 10px;
        }

        .govuk-card--hover:hover {
            transform: translateY(-4px); /* Hover effect */
            transition: transform 0.3s ease;
        }

        /* Layout for grid */
        .govuk-grid-row {
            margin-bottom: 40px;
        }

        /* Sidebar - popular services */
        .govuk-related-items {
            padding: 20px;
            background-color: #444444; /* Dark grey box background */
            border: 1px solid #333333; /* Darker grey border */
            border-radius: 6px;
        }

        /* Footer with dark blue background */
        .govuk-footer {
            background-color: #17203D; /* Dark blue */
            color: white;
            padding: 20px 0;
        }

        .govuk-footer__link {
            color: white;
        }

        .govuk-footer__link:hover {
            color: #6552D0; /* Purple on hover */
        }

        .govuk-footer__list-item {
            margin-bottom: 10px;
        }

        .govuk-footer__meta-item {
            margin-top: 20px;
        }

        .govuk-button {
            background-color: #6552D0; /* Purple */
            color: white;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
            border-radius: 4px;
            transition: background-color 0.3s ease;
        }

        .govuk-button:hover {
            background-color: #4a42b0; /* Slightly darker purple on hover */
        }

        .govuk-input {
            padding: 10px;
            border: 1px solid #b1b4b6;
            border-radius: 4px;
            width: 100%;
            margin-bottom: 10px;
            background-color: #333333; /* Dark grey input background */
            color: white; /* White text inside inputs */
        }

        .govuk-input__wrapper {
            position: relative;
        }

        .govuk-input__clear {
            position: absolute;
            top: 10px;
            right: 10px;
            color: #b1b4b6;
            cursor: pointer;
        }

        .govuk-link {
            color: #8e44ad; /* Brighter purple */
            text-decoration: none;
        }

        .govuk-link:hover {
            color: #6552D0; /* GOV.UK purple */
        }

        /* Circular Search Icon (top-right) */
        .search-icon {
            position: fixed; /* Make it fixed so it stays in place while scrolling */
            top: 20px;
            right: 20px;
            width: 40px;
            height: 40px;
            background-color: #6552D0;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 1000; /* Ensure it's above other content */
        }

        .search-icon img {
            width: 20px;
            height: 20px;
        }

        /* Hidden expanded search bar */
        #searchBar {
            position: absolute;
            top: 20px;
            right: 20px;
            display: none;
            background-color: #333333;
            border-radius: 4px;
            padding: 10px;
            width: 300px;
            z-index: 9999;
            transition: width 0.3s ease;
        }

        #searchBar input {
            width: calc(100% - 60px);
            padding: 10px;
            border: 1px solid #b1b4b6;
            background-color: #444444;
            color: white;
            border-radius: 4px;
        }

        #searchBar button {
            background-color: transparent;
            color: white;
            border: none;
            cursor: pointer;
        }

        /* Close Button for Search */
        .close-search {
            position: absolute;
            top: 5px;
            right: 5px;
            background: transparent;
            border: none;
            color: white;
            font-size: 20px;
            cursor: pointer;
        }

        /* Highlight matched text */
        .highlight {
            background-color: yellow;
            color: black;
            border-radius: 3px;
        }

        /* Footer Support Links */
        .govuk-footer__inline-list-item {
            margin-bottom: 10px;
        }

        /* Media Queries for Responsiveness */
        @media (max-width: 768px) {
            .govuk-grid-row {
                display: block;
            }
            .govuk-grid-column-two-thirds,
            .govuk-grid-column-one-third {
                width: 100%;
                margin-bottom: 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Magnifying Glass Icon to Trigger Search Bar -->
    <div class="search-icon" onclick="toggleSearchBar()">
        <img src="https://upload.wikimedia.org/wikipedia/commons/a/a4/Magnifying_glass_icon.svg" alt="Search">
    </div>

    <!-- Search Bar with Close Button -->
    <div id="searchBar">
        <button class="close-search" onclick="closeSearchBar()">×</button>
        <form id="searchForm" onsubmit="return false;">
            <input type="text" id="searchQuery" class="govuk-input" placeholder="Search this page..." />
            <button type="submit" class="govuk-button" onclick="searchText()">Search</button>
        </form>
    </div>

    <header class="govuk-header">
        <h1 class="govuk-heading-xl">Welcome to GOV.UK Clone</h1>

        <!-- Regular Search Bar for Article Search -->
        <form asp-action="Index" method="get" class="govuk-form-group">
            <label class="govuk-label" for="search">Search articles</label>
            <div class="govuk-input__wrapper">
                <input type="text" name="searchTerm" id="search" class="govuk-input govuk-input--with-clear" />
                <button type="button" class="govuk-input__clear" aria-label="Clear search">×</button>
            </div>
            <button type="submit" class="govuk-button">Search</button>
        </form>
    </header>

    <main class="govuk-main-wrapper" id="main-content">
        <div class="govuk-grid-row">
            <!-- Articles Section -->
            <div class="govuk-grid-column-two-thirds">
                <h2 class="govuk-heading-l">Articles</h2>

                <!-- Articles Grid -->
                <div class="govuk-grid-row govuk-card-group">
                    <div class="govuk-grid-column-one-third">
                        <div class="govuk-card govuk-card--hover">
                            <div class="govuk-card__content">
                                <h3 class="govuk-heading-m"><a href="https://www.gov.uk/benefits" class="govuk-link">Benefits</a></h3>
                                <p class="govuk-body">Search for information on benefits and how to apply for them.</p>
                            </div>
                        </div>
                    </div>
                    <div class="govuk-grid-column-one-third">
                        <div class="govuk-card govuk-card--hover">
                            <div class="govuk-card__content">
                                <h3 class="govuk-heading-m"><a href="https://www.gov.uk/business-and-self-employed" class="govuk-link">Business & Self-employed</a></h3>
                                <p class="govuk-body">Get information on starting and running your business.</p>
                            </div>
                        </div>
                    </div>
                    <div class="govuk-grid-column-one-third">
                        <div class="govuk-card govuk-card--hover">
                            <div class="govuk-card__content">
                                <h3 class="govuk-heading-m"><a href="https://www.gov.uk/government/organisations" class="govuk-link">Government Organisations</a></h3>
                                <p class="govuk-body">Find out about government departments, agencies, and public bodies.</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Popular Services Section -->
                <h2 class="govuk-heading-l">Popular Services</h2>
                <div class="govuk-grid-row govuk-card-group">
                    <div class="govuk-grid-column-one-third">
                        <div class="govuk-card govuk-card--hover">
                            <div class="govuk-card__content">
                                <h3 class="govuk-heading-m"><a href="https://www.gov.uk/births-deaths-marriages-and-care" class="govuk-link">Births, deaths, marriages and care</a></h3>
                                <p class="govuk-body">Information about registering births, deaths, and getting married.</p>
                            </div>
                        </div>
                    </div>
                    <div class="govuk-grid-column-one-third">
                        <div class="govuk-card govuk-card--hover">
                            <div class="govuk-card__content">
                                <h3 class="govuk-heading-m"><a href="https://www.gov.uk/government/organisations/government-digital-service" class="govuk-link">Government Digital Service</a></h3>
                                <p class="govuk-body">Information about the digital transformation of government services.</p>
                            </div>
                        </div>
                    </div>
                    <div class="govuk-grid-column-one-third">
                        <div class="govuk-card govuk-card--hover">
                            <div class="govuk-card__content">
                                <h3 class="govuk-heading-m"><a href="https://www.gov.uk/accessibility" class="govuk-link">Accessibility Statement</a></h3>
                                <p class="govuk-body">Read the accessibility statement for GOV.UK.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Sidebar - Popular Services -->
            <div class="govuk-grid-column-one-third">
                <aside class="govuk-related-items">
                    <h2 class="govuk-heading-m">Popular Services</h2>
                    <ul class="govuk-list">
                        <li><a class="govuk-link" href="https://www.gov.uk/benefits">Benefits</a></li>
                        <li><a class="govuk-link" href="https://www.gov.uk/business-and-self-employed">Business & Self-employed</a></li>
                        <li><a class="govuk-link" href="https://www.gov.uk/government/organisations">Government Organisations</a></li>
                    </ul>
                </aside>
            </div>
        </div>
    </main>

    <footer class="govuk-footer">
        <div class="govuk-footer__navigation">
            <div class="govuk-footer__section">
                <h2 class="govuk-footer__heading">Services and information</h2>
                <ul class="govuk-footer__list">
                    <li class="govuk-footer__list-item"><a class="govuk-footer__link" href="https://www.gov.uk/benefits">Benefits</a></li>
                    <li class="govuk-footer__list-item"><a class="govuk-footer__link" href="https://www.gov.uk/business-and-self-employed">Business and self-employed</a></li>
                    <li class="govuk-footer__list-item"><a class="govuk-footer__link" href="https://www.gov.uk/government/organisations">Government organisations</a></li>
                </ul>
            </div>
        </div>
        <div class="govuk-footer__meta">
            <div class="govuk-footer__meta-item govuk-footer__meta-item--grow">
                <h2 class="govuk-visually-hidden">Support links</h2>
                <ul class="govuk-footer__inline-list">
                    <li class="govuk-footer__inline-list-item"><a class="govuk-footer__link" href="https://www.gov.uk/help">Support</a></li>
                    <li class="govuk-footer__inline-list-item"><a class="govuk-footer__link" href="https://www.gov.uk/help">Help</a></li>
                    <li class="govuk-footer__inline-list-item"><a class="govuk-footer__link" href="https://www.gov.uk/government/organisations/government-digital-service/privacy-policy">Privacy</a></li>
                    <li class="govuk-footer__inline-list-item"><a class="govuk-footer__link" href="https://www.gov.uk/cookies">Cookies</a></li>
                    <li class="govuk-footer__inline-list-item"><a class="govuk-footer__link" href="https://www.gov.uk/accessibility">Accessibility statement</a></li>
                    <li class="govuk-footer__inline-list-item"><a class="govuk-footer__link" href="https://www.gov.uk/contact">Contact</a></li>
                    <li class="govuk-footer__inline-list-item"><a class="govuk-footer__link" href="https://www.gov.uk/report-an-issue">Report an issue</a></li>
                </ul>
            </div>
        </div>
    </footer>

    <script>
        // Toggle the search bar visibility
        function toggleSearchBar() {
            const searchBar = document.getElementById('searchBar');
            searchBar.style.display = (searchBar.style.display === 'block') ? 'none' : 'block';
        }

        // Close search bar (for cross or clicking outside)
        function closeSearchBar() {
            document.getElementById('searchBar').style.display = 'none';
        }

        // Close search bar when clicking outside of it
        document.addEventListener('click', function(event) {
            const searchBar = document.getElementById('searchBar');
            const searchIcon = document.querySelector('.search-icon');
            
            if (!searchBar.contains(event.target) && !searchIcon.contains(event.target)) {
                closeSearchBar();
            }
        });

        // Perform the search and highlight matches
        function searchText() {
            const searchQuery = document.getElementById('searchQuery').value.toLowerCase();
            const bodyText = document.body.innerHTML.toLowerCase();
            
            const matches = bodyText.match(new RegExp(searchQuery, 'g'));
            if (matches) {
                alert(matches.length + ' matches found!');
                highlightMatches(searchQuery);
                scrollToFirstMatch(searchQuery);
            } else {
                alert('No matches found.');
            }
        }

        // Highlight matched text
        function highlightMatches(query) {
            const regex = new RegExp(query, 'gi');
            const elements = document.body.getElementsByTagName('*');
            for (let i = 0; i < elements.length; i++) {
                const element = elements[i];
                if (element.innerHTML && element.innerHTML.match(regex)) {
                    element.innerHTML = element.innerHTML.replace(regex, (match) => {
                        return `<span class="highlight">${match}</span>`;
                    });
                }
            }
        }

        // Scroll to the first match of the search term
        function scrollToFirstMatch(query) {
            const regex = new RegExp(query, 'gi');
            const elements = document.body.getElementsByTagName('*');
            for (let i = 0; i < elements.length; i++) {
                const element = elements[i];
                if (element.innerHTML && element.innerHTML.match(regex)) {
                    element.scrollIntoView({ behavior: 'smooth', block: 'center' });
                    break;
                }
            }
        }
    </script>
</body>
</html>

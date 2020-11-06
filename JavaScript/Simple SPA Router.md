A simple router for use in SPAs.

    <nav>
      <a href="#/">Home</a> -
      <a href="#/page1">Page 1</a> -
      <a href="#/page2">Page 2</a> -
      <a href="#/page3">Page 3</a>
    </nav>
    <div id="app"></div>
    <script>

        // Components
        const HomeComponent = {
            render: () => {
                return `
                <section>
                    <h1>Home</h1>
                    <p>This is the home page.</p>
                </section>
                `;
            }
        } 

        const Page1Component = {
            render: () => {
                return `
                <section>
                    <h1>Page 1</h1>
                    <p>This is page 1.</p>
                </section>
                `;
            }
        } 

        const Page2Component = {
            render: () => {
                return `
                <section>
                    <h1>Page 2</h1>
                    <p>This is page 2.</p>
                </section>
                `;
            }
        } 

        const Page3Component = {
            render: () => {
                return `
                <section>
                    <h1>Page 3</h1>
                    <p>This is page 3.</p>
                </section>
                `;
            }
        } 

        const ErrorComponent = {
            render: () => {
                return `
                <section>
                    <h1>Error</h1>
                    <p>This is the error page.</p>
                </section>
                `;
            }
        }

        const parseLocation = () => location.hash.slice(1).toLowerCase() || '/';

        const findComponentByPath = (path, routes) => routes.find(r => r.path.match(new RegExp(`^\\${path}$`, 'gm'))) || undefined;

        const routes = [
            { path: '/', component: HomeComponent, },
            { path: '/page1', component: Page1Component, },
            { path: '/page2', component: Page2Component, },
            { path: '/page3', component: Page3Component, },
        ];

        const router = () => {
            const path = parseLocation();
            const { component = ErrorComponent } = findComponentByPath(path, routes) || {};
            document.getElementById('app').innerHTML = component.render();
        };

        window.addEventListener('hashchange', router);
        window.addEventListener('load', router);
    </script>

<script lang="ts">
  import { Button, Col, Container, Icon, Row } from 'sveltestrap';
  import { linkTo } from '@storybook/addon-links';

  import PrismCode from '../PrismCode.svelte';
  import Example from '../Example.svelte';
  import Sample from './Sample.svelte';
  import sampleSource from '!!raw-loader!./Sample.svelte';
</script>

<div>
  <section class="bg-light text-center mb-3 p-5">
    <Container>
      <Row>
        <Col>
          <h1
            class="display-4 d-flex align-items-center justify-content-center"
            style="color: purple; font-weight: 200; letter-spacing: .2rem"
          >
            <svg
              height=".8em"
              viewBox="0 0 39.6 45"
              xmlns="http://www.w3.org/2000/svg"
              class="me-2"
            >
              <g transform="translate(2.5, 2.5)">
                <polyline
                  points="0,30 17.3,40 34.6,30 34.6,20 17.3,30 0,20 0,10
                           17.3,0 34.6,10 17.3,20 0,10"
                  fill="none"
                  stroke="currentcolor"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="3"
                />
              </g>
            </svg>
            SVELTESTRAP
          </h1>
          <p class="lead">
            <a href="https://v5.getbootstrap.com" target="new" class="text-body"
              >Bootstrap 5</a
            >
            components for
            <a href="https://svelte.dev" target="new" class="text-body"
              >Svelte 3</a
            >.
          </p>
          <p>
            <Button
              outline
              color="danger"
              href="https://github.com/bestguy/sveltestrap"
            >
              GitHub
            </Button>
            <Button color="danger" href="/?path=/story/components--layout">
              Components
            </Button>
          </p>
          <h6 class="text-danger mt-4">
            <Icon name="exclamation-triangle-fill" />
            <b>Note:</b>
            Bootstrap 4 CSS users must use Sveltestrap 4 - see docs here:
            <a href="./v4">Sveltestrap version 4</a>
          </h6>
        </Col>
      </Row>
    </Container>
  </section>
  <Container>
    <Row class="justify-content-sm-center">
      <Col sm={8} class="docSearch-content">
        <Example source={sampleSource} stacked>
          <Sample />
        </Example>

        <h2>Installation</h2>
        <hr />
        <h3 class="mt-5">NPM</h3>
        <p>Install sveltestrap and peer dependencies via NPM</p>
        <pre>
          <PrismCode class="language-bash">
            npm install sveltestrap svelte
          </PrismCode>
        </pre>

        <h4>Adding Bootstrap</h4>
        <p>
          Sveltestrap does not include or embed Bootstrap CSS so this needs to
          be installed by you, either by including Bootstrap CSS to your layout
          (1) , or installed from npm (2).
        </p>

        <h5>1. Include in layout</h5>

        <h6>Either static HTML layout</h6>
        <pre>
          <PrismCode class="language-html">
            {`<head>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/css/bootstrap.min.css">
</head>`}
          </PrismCode>
        </pre>

        <h6>or using &lt;svelte:head&gt; in your Svelte source:</h6>
        <pre>
          <PrismCode class="language-html">
            {`<svelte:head>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/css/bootstrap.min.css">
</svelte:head>`}
          </PrismCode>
        </pre>

        <h6>
          or use the <Button
            color="link"
            class="p-0"
            style="vertical-align: unset;"
            on:click={linkTo('Components', 'Styles')}>Styles</Button
          > component:
        </h6>
        <pre>
          <PrismCode class="language-html">
            {`<script>
  import { Styles } from 'sveltestrap';
</script>

<Styles />`}
          </PrismCode>
        </pre>

        <p>
          You can also use any Bootstrap 5 compatible theme instead of the
          default Bootstrap theme. For example:
          <a href="https://www.bootstrapcdn.com/bootswatch/" target="new">
            https://www.bootstrapcdn.com/bootswatch/
          </a>
        </p>

        <h5>2. or install via npm</h5>
        <pre>
          <PrismCode class="language-bash">
            {`npm install bootstrap`}
          </PrismCode>
        </pre>
        <p>
          Import Bootstrap CSS in the
          <code>src/index.js</code>
          file:
        </p>
        <pre>
          <PrismCode class="language-javascript">
            import 'bootstrap/dist/css/bootstrap.min.css';
          </PrismCode>
        </pre>

        <h4>Note on Icons</h4>
        <p>
          If you wish to use the <Button
            color="link"
            class="p-0"
            style="vertical-align: unset;"
            on:click={linkTo('Components', 'Icon')}>Icon</Button>
          component, you also must include a link to Bootstrap Icon CSS, for example:
        </p>
        <pre>
          <PrismCode class="language-html">
            {`<svelte:head>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.5.0/font/bootstrap-icons.css">
</svelte:head>`}
          </PrismCode>
        </pre>
        or the <Button
          color="link"
          class="p-0"
          style="vertical-align: unset;"
          on:click={linkTo('Components', 'Styles')}>Styles</Button
        > component includes the Bootstrap Icon CSS by default:
        <pre>
          <PrismCode class="language-html">
            {`<script>
  import { Styles } from 'sveltestrap';
</script>
            
<Styles />`}
          </PrismCode>
        </pre>
        <p>
          This component uses and assumes the CSS based webfont. You can host
          the icon CSS and webfonts on your own domain if needed.
        </p>

        <h3>Using in Svelte app</h3>
        <p>
          Import required sveltestrap components within
          <code>src/App.svelte</code>
          file or your custom component files:
        </p>
        <pre>
          <PrismCode class="language-javascript">
            {`import { Button } from 'sveltestrap';`}
          </PrismCode>
        </pre>
        <p>
          Now you are ready to use the imported sveltestrap components within
          your component hierarchy.
        </p>

        <h4>Server-side Rendering (SSR) Note:</h4>
        <p>
          If you are using Sveltestrap in an SSR environment (such as Sapper),
          it's recommended you import the component src directly:
        </p>
        <pre>
          <PrismCode class="language-javascript">
            {`import { Card } from 'sveltestrap/src'`}
          </PrismCode>
        </pre>

        <h2 class="mt-5">About the Project</h2>
        <hr />
        <p>
          This library was inspired by the <a
            href="https://reactstrap.github.io">reactstrap</a
          > library for React. This does not depend on jQuery or Bootstrap's JavaScript,
          and instead uses Svelte.
        </p>
      </Col>
    </Row>
  </Container>
</div>

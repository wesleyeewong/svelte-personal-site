<script lang="ts">
  import { Accordion, AccordionItem } from "@skeletonlabs/skeleton";
  import github_logo from "$lib/images/github-logo.png";
  import linkedin_logo from "$lib/images/linkedin-logo.png";

  export let data;
</script>

<svelte:head>
  <title>Work experiences</title>
</svelte:head>

<div class="container h-auto mx-auto justify-center items-center m-5">
  <h1 class="h1 p-5">My work experiences</h1>
  <div class="border-2 p-5">
    <article>
      <p>🚀 Dynamic software engineer with a strong focus on backend development, leveraging expertise to build innovative features that elevate user experiences. 💡 Proficient in Ruby on Rails and experienced in developing robust backend solutions. 🌟 Currently expanding frontend skills with Sveltekit, maintaining a well-rounded skill set. 🌍 Driven by a genuine passion for creating products that positively impact and enhance individuals' lives.</p>
    </article>
  </div>
</div>

<div class="h-auto m-5">
  <div class="container h-full mx-auto jusity-center items-center">
    <Accordion duration={ 400 } spacing="space-y-5">
      {#each data.experiences as experience}
        <AccordionItem>
          <svelte:fragment slot="summary">
            <h3 class="h3">{ experience.name }</h3>
          </svelte:fragment>

          <svelte:fragment slot="content">
            <div class="card p-4 variant-ringed-primary">
              <header class="card-header">
                <h4 class="h4">{ experience.title }</h4>
              </header>

              <section class="p-4">
                <Accordion duration={ 300 } spacing="space-y-3" autocollapse={ true }>
                  {#each experience.contents as content}
                    <AccordionItem>
                      <svelte:fragment slot="summary">
                        <h5 class="h5">{ content.abridged }</h5>
                      </svelte:fragment>
                      <svelte:fragment slot="content">
                        <article class="space-y-5">
                          <p>{ @html content.full }</p>
                        </article>
                      </svelte:fragment>
                    </AccordionItem>
                    <hr>
                  {/each}
                </Accordion>
              </section>

              <footer class="card-footer">
                {#each experience.medias as media}
                  {#if media.type == "video/mp4"}
                    <video controls width="500">
                      <source src={ media.src }>
                    </video>
                  {:else}
                    <img src={ media.src } alt={ media.alt } width="300">
                  {/if}
                {/each}
              </footer>
            </div>
          </svelte:fragment>
        </AccordionItem>
      {/each}
    </Accordion>
  </div>
</div>

<div class="h-1/4 container mx-auto jusity-center items-center p-20 m-10">
  <div class="logo-cloud grid-cols-2 gap-1 [&>.logo-item]:variant-ringed-primary">
    <a class="logo-item" href="https://github.com/wesleyeewong" target="_blank">
      <span><img src={ github_logo } alt="Github logo" width="25"></span>
      <span>github</span>
    </a>
    <a class="logo-item" href="https://www.linkedin.com/in/wesleyeewong" target="_blank">
      <span><img src={ linkedin_logo } alt="Linkedin logo" width="25"></span>
      <span>linkedin</span>
    </a>
  </div>
</div>

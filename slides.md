        <section># Dependency Injection with React Context</section>

        <section>
          ## Components Encapsulation 👍
          <div>example component with no props</div>
          <div class="notes">
            we can take a component like this and use it anywhere we want
            withouth needing to know anything about its implementation details.
            makes it easier to read & reason about our code, because all the
            details that we don't need to worry about right now are hidden away
          </div>
          <div>Customisation thumbs down</div>
          <div>
            some kind of picture - maybe showing component in different colours,
            but crossed out
          </div>
          <div class="notes">
            but a component like this can't really be customised, which limits
            its usefulness
          </div>
        </section>

        <section>
          reasons to customise a component - changing the colour of an alert to
          convey different information, changing the onsubmit on a form in
          different contexts, changing the data-fetching when testing,
          libraries, logging & analytics, different redux stores in different
          parts of the code, Emphasise that it could be state or it could be
          strategies
        </section>

        <section>
          <div class="notes">
            of course we do have a way to customise all these things - we can
            use props
          </div>
          all the previous examples with props
        </section>

        <section>
          <div class="notes">
            and that's basically all dependency injection is
          </div>
          "Dependency injection means giving an object its instance variables."
          <div class="notes">
            doesn't quite work with react, because it's referring to instance
            variables of objects, and react works with functions, change to
            "giving a component its variables" emphasise a variable could be a
            value or it could be a function
          </div>
          "a 25-dollar term for a 5-cent concept" James Shore
          https://www.jamesshore.com/v2/blog/2006/dependency-injection-demystified
        </section>

        <section>
          So why do we need a fancy name like dependency injection if it's
          really just using props? not all props are dependency injection - very
          wishy washy, but you wouldn't normally refer to changing colour or
          onclick handler as dependency injection. it's normally fundammental
          state or strategies - examples of things you would call dependency
          injection
        </section>

        <section>Not all dependency injection is via props</section>

        <section>
          dependency injection comes from OO classic dependency injection using
          constructor == equivalent to props other ways to do it, eg setter
          doesn't really work with react, but we do have another tool available
          to us - hooks function MyTodoApp() { const { Query, useFilterBy } =
          MyTodoApp.dependencies; // ... }MyTodoApp.dependencies = { Query:
          QueryDI, useFilterBy: useFilterByDI, }
          <div class="notes">
            if we could build a hook that shared state between multiple
            components, we'd have dependency injection via hooks
          </div>
        </section>

        <section>
          what we want the usage to look like inside the component (ie calling
          `useDependencies`)
        </section>

        <section>
          how we can implement that - our createDependencyInjectionContainer
          function (sidenote explaining dependency injection containers)
        </section>

        <section>omg we just wrote useContext</section>

        <section>dependency injection libraries</section>

        <section>
          mostly remove the need for context+provider obsidian & wox do this via
          annotations example code for each nice if you miss angular wox
          requires a whole bunch of build stuff that seems like a pain troch
          does it via explicit setting example code for troch
        </section>

        <section>
          main advantages of using a library - being explicit about what things
          are dependencies. maybe you find that helpful, honestly i'm not
          convinced - not needing context/provider big disadvantage of context
          is that it's invisible - you can't easily see all the providers that
          your code needs personally, i handle this by good error messaging -
          create specific hooks for each context and throw an error when the
          provider doesn't exist what does react actually do if you try to use
          context without a provider? is the error message good?
        </section>

        <section>
          react-magnetic-di
          <div class="notes">
            one library i do find super useful though, specifically for
            injecting dependencies in tests no specific set-up, code doesn't
            even know that its dependencies are being injected can replace
            basically anything that's imported examples
          </div>
        </section>

        <section>
          dependency injection solves the problem of needing to customise
          components not complex - it's just passing variables to components
          there are a bunch of ways to achieve it - props, setters, context,
          libraries
        </section>

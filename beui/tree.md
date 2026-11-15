beui's tree layer is the part of beui that provides jsx-like syntax and basic reactive tree functionality:

These are part of beui tree:

```
#[component]
fn ComponentFn() -> () {}

view! {
    <ComponentFn />
}

<Show if={condition} then={|| abc} fallback={|| def} />
```

beui's tree layer does not depend on any specific gui framework, so it can be used to build any tree:

```
// html
html.render_to_string(view! {
    <Html::Div class="px-4 py-2 flex">
        <Html::P>
            "Hello!"
        </Html::P>
    </Html::Div>
}) // -> "<div class="px-4 py-2 flex"><p>Hello!</p></div>"

// discord
discord.render_to_json(view! {
    <Message
        body=<>
            "Tic tac toe"
        </>
        actions=<>
            <ActionRow>
                <Button />
            </ActionRow>
        </>
    />
}); // -> {content:"Tic tac toe",actions:[{}]}

// filesystem
myfolder.write(view! {
    <Folder name="work">
        <File name="setup.txt">
            "hello"
        </File>
        <Symlink name="help.txt" to="setup.txt" />
    </File>
}); // -> $ ls myfolder: 'work'. $ ls myfolder/work: 'setup.txt help.txt'
```

You can even mix multiple in one file:

```
html.render_to_string(view! {
    <Html::Pre>
        <Html::Code>
            {markdown.render_to_string(view! {
                <Markdown::Heading level=1>
                    "Hello"
                </Markdown::Heading>
                <Markdown::Paragraph>
                    "Goodbye"
                </Markdown::Paragraph>
            })}
        </Html::Code>
    </Html::Pre>
}) // -> "<pre><code># Hello\n\nGoodbye</code></pre>"
```

Single and multiple children are differentiated, so a component is able to accept just a single child if it wants.

Keep in mind that all syntax or code samples here are approximate and likely wrong, not to be directly replicated.
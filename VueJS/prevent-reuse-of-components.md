# Prevent VueJS to reuse a component when changing page
Vue tries to render elements as efficiently as possible, often re-using them instead of rendering from scratch.

But when changing page (with VueX), having a table be depopulated and repopulated with animations is unwanted behavior. A simple way (and the recommended way) to do that is to assign a `key` to the component we want to not be reused.

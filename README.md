
# Keycloakify Starter

This repo constitutes an easily reusable setup for a Keycloak theme project.
This starter is based on Vite. There is also [a Webpack based starter](https://github.com/keycloakify/keycloakify-starter-cra).  


# Quick start

```bash
git https://github.com/henry-azer/keycloakify-starter

cd keycloakify-starter

npm i # install dependencies (it's like npm install)

npm run storybook # Start Storybook
                  # This is by far the best way to develop your theme
                  # This enable to quickly see your pages in isolation and in different states.  
                  # You can create stories even for pages that you haven't explicitly overloaded. See src/keycloak-theme/login/pages/LoginResetPassword.stories.tsx
                  # See Keycloakify's storybook for if you need a starting point for your stories: https://github.com/keycloakify/keycloakify/tree/main/stories

npm run dev # See the Hello World app
            # Uncomment line 97 of src/keycloak-theme/login/kcContext where it reads: `mockPageId: "login.ftl"`, reload https://localhost:3000
            # You can now see the login.ftl page with the mock data. (Don't forget to comment it back when you're done)
          
# Install mvn (Maven) if not already done. On mac it's 'brew install maven', on Ubuntu/Debian it's 'sudo apt-get install maven'

npm run build-keycloak-theme # Actually build the theme (generates the .jar to be imported in Keycloak)
                             # Read the instruction printed on the console to see how to test
                             # your theme on a real Keycloak instance.

npx eject-keycloak-page # Prompt that let you select the pages you want to customize
                        # This CLI tools is not guaranty to work, you can always copy pase pages 
                        # from the Keycloakify repo.
                        # After you ejected a page you need to edit the src/keycloak-theme/login(or admin)/KcApp.tsx file
                        # You need to add a case in the switch for the page you just imported in your project.  
                        # Look how it's done for the Login page and replicate for your new page.  

npx initialize-email-theme # For initializing your email theme
                           # Note that Keycloakify does not feature React integration for email yet.

npx download-builtin-keycloak-theme # For downloading the default theme (as a reference)
                                    # Look for the files in dist_keycloak/src/main/resources/theme/{base,keycloak}
```

# Theme variant  

Keycloakify enables you to create different variant for a single theme.  
This enable you to have a single jar that embed two or more theme variant.  

![Theme variant](https://content.gitbook.com/content/FcBKODbZbNDgm0rc6a9K/blobs/9iKgs2rv2Kfb2pbs4dRz/image.png)  

You can enable this feature by providing multiple theme name in the Keycloakify build option.  
[See documentation](https://docs.keycloakify.dev/build-options#themename)  

# The CI workflow

-   To release **don't create a tag manually**, the CI do it for you. Just update the `package.json`'s version field and push.
-   The `.jar` files that bundle the Keycloak theme will be attached as an asset with every GitHub release. [Example](https://github.com/InseeFrLab/keycloakify-starter/releases/tag/v0.1.0). The permalink to download the latest version is: `https://github.com/USER/PROJECT/releases/latest/download/keycloak-theme.jar`.
    For this demo repo it's [here](https://github.com/codegouvfr/keycloakify-starter/releases/latest/download/keycloak-theme.jar)

![image](https://user-images.githubusercontent.com/6702424/229296556-a69f2dc9-4653-475c-9c89-d53cf33dc05a.png)


# The storybook  

![image](https://github.com/keycloakify/keycloakify/assets/6702424/a18ac1ff-dcfd-4b8c-baed-dcda5aa1d762)  

```bash
npm i
npm run storybook
```

# Conclusion  

The Keycloakify starter project offers an efficient framework for developing custom Keycloak themes using Vite. It provides a modern development environment with integrated Storybook for component testing, catering to both novice and experienced developers with its clear documentation. The project's standout feature is its support for multiple theme variants in a single jar, enhancing theme reusability. Additionally, the CI workflow automates the release process, creating tags and attaching .jar files to GitHub releases. With tools like `npx eject-keycloak-page` and `npx initialize-email-theme`, Keycloakify simplifies customization and theme development, making it a valuable resource for anyone creating or modifying Keycloak themes.
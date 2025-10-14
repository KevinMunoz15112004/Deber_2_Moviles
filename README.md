# Deber 2 Apps. Móviles

Implementación de una aplicación con ícono personalizado y un splash screen

## Paso 1 - Creación del proyecto

Primero se debe ejecutar <code>ionic start miApp blank --type=angular</code>. Luego se deberá iniciar el proyecto con la opción de <code>standalone</code>

Ahora se procede a abrir VS Code para visualizar el proyecto creado:

<img width="231" height="360" alt="image" src="https://github.com/user-attachments/assets/5466d644-305c-4d95-b046-ea596561c8d1" />

## Paso 2 - Instalación y configuración de Splash Screen

### Documentación oficial: https://ionicframework.com/docs/native/splash-screen

El Splash Screen es la pantalla que se muestra al iniciar la aplicación, generalmente con el logotipo o una animación rápida. Para emplearla se necesitan archivos PNG o JPG llamados "splash.png" y "splash-dark.png". Una vez se cuenten con esos archivos se debe ejecutar el siguiente comando: <code>npm install @capacitor/splash-screen</code>, lo que permitirá usar el splash screen. Luego se debe ir a la documentación oficial de Ionic y buscar en la sección "Examples" el código proporcionado para <code>capacitor.config.ts</code>, este código es el siguiente: 

<code>plugins: {
    SplashScreen: {
      launchShowDuration: 3000,
      launchAutoHide: true,
      launchFadeOutDuration: 3000,
      backgroundColor: "#ffffffff",
      androidSplashResourceName: "splash",
      androidScaleType: "CENTER_CROP",
      showSpinner: true,
      androidSpinnerStyle: "large",
      iosSpinnerStyle: "small",
      spinnerColor: "#999999",
      splashFullScreen: true,
      splashImmersive: true,
      layoutName: "launch_screen",
      useDialog: true,
    },
  },</code>

Este código habrá que pegarlo en el archivo anteriormente mencionado. Una vez hecho se pegará en la sección correspondiente mostrandose finalmente así:

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/4291e025-c886-42c4-8ba9-e1f9e339b1d1" />

El código se puede modificar según sea requerido.

Luego, en el mismo sitio de la documentación oficial, se deberá buscar la sección "Example" para buscar la forma en la que se llama al Splash Screen. Primero se deberá copiar la siguiente importación <code>import { SplashScreen } from '@capacitor/splash-screen';</code>. Este código habrá que pegarlo en el archivo <code>app.component.ts</code>. Luego en el mismo archivo se creará una función que puede llamarse <code>showSplash</code> la cual deberá ser una función asíncrona para pegar el siguiente código:

<code>await SplashScreen.show({
  autoHide: false,
});</code>

Finalmente el archivo <code>app.component.ts</code> debe mostrarse así:

<img width="539" height="400" alt="image" src="https://github.com/user-attachments/assets/064de093-eb69-46fb-b47d-aea645927056" />

Ahora se procede a ejecutar <code>npm i @capacitor/android</code> para ya generar la plataforma android, seguido de esto se procede a ejecutar <code>ionic build</code>, y finalmente <code>npx cap add android</code>

## Paso 3 - Generación del Splash Screen y del ícono personalizado

### Documentación oficial: https://capacitorjs.com/docs/guides/splash-screens-and-icons

Primero se debe ejecutar <code>npm install @capacitor/assets</code>

Para proceder con la generación de ambos, como se mencionó en el Paso 2 se debe tener dos imagenes que servirán para el Splash Screen: "splash.png" y "splash-dark.png" las cuales deben ser de 2732px x 2732px. Pero adicionalmente se necesitan 3 imágenes para el ícono que se deben llamar "icon-only.png", "icon-foreground.png" y "icon-background.png", los íconos deben ser de 1024px x 1024px. Las imágenes de antes deben estar en una carpeta "assets" y ponerla en la raíz del proyecto. No es necesario tener diferentes imagénes, si se tiene una sola imagen del Splash Screen esa misma puede servir para las 2 que se necesitan; pasa lo mismo con el Ícono y las 3 necesarias, una vez se tenga eso, se procede a ejecutar el comando: <code>npx capacitor-assets generate</code>, este comando generará todos los recursos para el ícono y splash screen en diferentes resoluciones dentro de la carpeta Android

Las imágenes usadas para esta aplicación fueron:

Ícono:

<img width="253" height="289" alt="image" src="https://github.com/user-attachments/assets/c8dad7e1-339c-426b-94dd-231e14f48656" />

Splash Screen:

<img width="233" height="236" alt="image" src="https://github.com/user-attachments/assets/30e65b3f-b6d2-43d3-86c7-8122f56292fc" />










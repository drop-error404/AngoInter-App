# AngoNurse 2Game - Guia Completo para RV2IDE

## 📱 Informações do Projeto

| Propriedade | Valor |
|-------------|-------|
| **Package** | `com.angonurse.game2` |
| **minSdk** | 21 |
| **targetSdk** | 34 |
| **compileSdk** | 36 |
| **Linguagem** | Kotlin |
| **Nome do App** | AngoNurse Quiz & Memory |

> ⚠️ **Nota**: O package foi alterado para `com.angonurse.game2` pois nomes de pacotes Android não podem começar com números.

---

## 📁 Estrutura do Projeto

```
app/
├── src/
│   └── main/
│       ├── java/com/angonurse/game2/
│       │   ├── MainActivity.kt
│       │   ├── WelcomeActivity.kt
│       │   ├── QuizActivity.kt
│       │   ├── MemoryGameActivity.kt
│       │   ├── ResultActivity.kt
│       │   ├── MemoryResultActivity.kt
│       │   ├── AboutActivity.kt
│       │   ├── SettingsActivity.kt
│       │   ├── adapters/
│       │   │   ├── QuizOptionAdapter.kt
│       │   │   └── MemoryCardAdapter.kt
│       │   ├── models/
│       │   │   ├── Question.kt
│       │   │   ├── MemoryCard.kt
│       │   │   └── DifficultyLevel.kt
│       │   ├── managers/
│       │   │   ├── QuizManager.kt
│       │   │   ├── MemoryGameManager.kt
│       │   │   └── SoundManager.kt
│       │   └── utils/
│       │       ├── PreferencesHelper.kt
│       │       └── ScreenUtils.kt
│       ├── res/
│       │   ├── layout/
│       │   │   ├── activity_main.xml
│       │   │   ├── activity_welcome.xml
│       │   │   ├── activity_quiz.xml
│       │   │   ├── activity_memory_game.xml
│       │   │   ├── activity_result.xml
│       │   │   ├── activity_memory_result.xml
│       │   │   ├── activity_about.xml
│       │   │   ├── activity_settings.xml
│       │   │   ├── item_quiz_option.xml
│       │   │   ├── item_memory_card.xml
│       │   │   └── dialog_difficulty.xml
│       │   ├── drawable/
│       │   │   ├── bg_gradient_dark.xml
│       │   │   ├── bg_glass_card.xml
│       │   │   ├── bg_button_primary.xml
│       │   │   ├── bg_button_secondary.xml
│       │   │   ├── bg_option_normal.xml
│       │   │   ├── bg_option_selected.xml
│       │   │   ├── bg_option_correct.xml
│       │   │   ├── bg_option_wrong.xml
│       │   │   ├── bg_memory_card.xml
│       │   │   ├── bg_memory_card_flipped.xml
│       │   │   ├── bg_progress_bar.xml
│       │   │   ├── bg_timer.xml
│       │   │   ├── ic_launcher_foreground.xml
│       │   │   └── ic_launcher_background.xml
│       │   ├── mipmap-xxxhdpi/
│       │   │   └── ic_launcher.png
│       │   ├── raw/
│       │   │   ├── sound_match.mp3
│       │   │   ├── sound_mismatch.mp3
│       │   │   └── musica.aac
│       │   ├── values/
│       │   │   ├── colors.xml
│       │   │   ├── strings.xml
│       │   │   ├── styles.xml
│       │   │   └── dimens.xml
│       │   └── values-night/
│       │       └── colors.xml
│       └── AndroidManifest.xml
├── build.gradle.kts
└── proguard-rules.pro
```

---

## 📄 Arquivos de Configuração

### AndroidManifest.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.angonurse.game2">

    <uses-permission android:name="android.permission.INTERNET" />

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher"
        android:supportsRtl="true"
        android:theme="@style/Theme.AngoNurseGame"
        android:configChanges="orientation|screenSize|screenLayout|keyboardHidden">

        <activity
            android:name=".MainActivity"
            android:exported="true"
            android:screenOrientation="portrait"
            android:theme="@style/Theme.AngoNurseGame.Splash">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <activity
            android:name=".WelcomeActivity"
            android:screenOrientation="portrait" />

        <activity
            android:name=".QuizActivity"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="adjustPan" />

        <activity
            android:name=".MemoryGameActivity"
            android:screenOrientation="portrait" />

        <activity
            android:name=".ResultActivity"
            android:screenOrientation="portrait" />

        <activity
            android:name=".MemoryResultActivity"
            android:screenOrientation="portrait" />

        <activity
            android:name=".AboutActivity"
            android:screenOrientation="portrait" />

        <activity
            android:name=".SettingsActivity"
            android:screenOrientation="portrait" />

    </application>

</manifest>
```

### build.gradle.kts (Module: app)

```kotlin
plugins {
    id("com.android.application")
    id("org.jetbrains.kotlin.android")
}

android {
    namespace = "com.angonurse.game2"
    compileSdk = 36

    defaultConfig {
        applicationId = "com.angonurse.game2"
        minSdk = 21
        targetSdk = 34
        versionCode = 1
        versionName = "1.0.0"
    }

    buildTypes {
        release {
            isMinifyEnabled = true
            isShrinkResources = true
            proguardFiles(
                getDefaultProguardFile("proguard-android-optimize.txt"),
                "proguard-rules.pro"
            )
        }
    }

    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_17
        targetCompatibility = JavaVersion.VERSION_17
    }

    kotlinOptions {
        jvmTarget = "17"
    }

    buildFeatures {
        viewBinding = true
    }
}

dependencies {
    implementation("androidx.core:core-ktx:1.12.0")
    implementation("androidx.appcompat:appcompat:1.6.1")
    implementation("com.google.android.material:material:1.11.0")
    implementation("androidx.constraintlayout:constraintlayout:2.1.4")
    implementation("androidx.recyclerview:recyclerview:1.3.2")
    implementation("androidx.cardview:cardview:1.0.0")
    implementation("androidx.lifecycle:lifecycle-runtime-ktx:2.7.0")
}
```

### build.gradle.kts (Project)

```kotlin
plugins {
    id("com.android.application") version "8.2.0" apply false
    id("org.jetbrains.kotlin.android") version "1.9.22" apply false
}
```

### settings.gradle.kts

```kotlin
pluginManagement {
    repositories {
        google()
        mavenCentral()
        gradlePluginPortal()
    }
}

dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
    }
}

rootProject.name = "AngoNurseGame"
include(":app")
```

---

## 🎨 Resources - Values

### colors.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <!-- Primary Colors -->
    <color name="primary">#10B981</color>
    <color name="primary_dark">#059669</color>
    <color name="primary_light">#34D399</color>
    <color name="primary_glow">#6EE7B7</color>
    
    <!-- Background Colors -->
    <color name="background">#0A0F1C</color>
    <color name="background_secondary">#111827</color>
    <color name="surface">#1F2937</color>
    <color name="surface_elevated">#374151</color>
    
    <!-- Text Colors -->
    <color name="text_primary">#F9FAFB</color>
    <color name="text_secondary">#9CA3AF</color>
    <color name="text_muted">#6B7280</color>
    
    <!-- Status Colors -->
    <color name="success">#22C55E</color>
    <color name="success_bg">#14532D</color>
    <color name="error">#EF4444</color>
    <color name="error_bg">#7F1D1D</color>
    <color name="warning">#F59E0B</color>
    <color name="warning_bg">#78350F</color>
    
    <!-- Glass Effect -->
    <color name="glass_bg">#1A1F2937</color>
    <color name="glass_border">#33374151</color>
    
    <!-- Card Colors -->
    <color name="card_bg">#1A2332</color>
    <color name="card_border">#2D3748</color>
    
    <!-- Option States -->
    <color name="option_normal">#1E293B</color>
    <color name="option_selected">#1D4ED8</color>
    <color name="option_correct">#166534</color>
    <color name="option_wrong">#991B1B</color>
    
    <!-- Memory Card -->
    <color name="memory_card_back">#1E3A5F</color>
    <color name="memory_card_front">#0D1B2A</color>
    
    <!-- Gradients -->
    <color name="gradient_start">#0A0F1C</color>
    <color name="gradient_middle">#1A1F2E</color>
    <color name="gradient_end">#0F172A</color>
</resources>
```

### values-night/colors.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <!-- Same colors for dark mode - app is always dark themed -->
    <color name="primary">#10B981</color>
    <color name="primary_dark">#059669</color>
    <color name="primary_light">#34D399</color>
    <color name="primary_glow">#6EE7B7</color>
    
    <color name="background">#0A0F1C</color>
    <color name="background_secondary">#111827</color>
    <color name="surface">#1F2937</color>
    <color name="surface_elevated">#374151</color>
    
    <color name="text_primary">#F9FAFB</color>
    <color name="text_secondary">#9CA3AF</color>
    <color name="text_muted">#6B7280</color>
    
    <color name="success">#22C55E</color>
    <color name="success_bg">#14532D</color>
    <color name="error">#EF4444</color>
    <color name="error_bg">#7F1D1D</color>
    <color name="warning">#F59E0B</color>
    <color name="warning_bg">#78350F</color>
    
    <color name="glass_bg">#1A1F2937</color>
    <color name="glass_border">#33374151</color>
    
    <color name="card_bg">#1A2332</color>
    <color name="card_border">#2D3748</color>
    
    <color name="option_normal">#1E293B</color>
    <color name="option_selected">#1D4ED8</color>
    <color name="option_correct">#166534</color>
    <color name="option_wrong">#991B1B</color>
    
    <color name="memory_card_back">#1E3A5F</color>
    <color name="memory_card_front">#0D1B2A</color>
    
    <color name="gradient_start">#0A0F1C</color>
    <color name="gradient_middle">#1A1F2E</color>
    <color name="gradient_end">#0F172A</color>
</resources>
```

### strings.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="app_name">AngoNurse Quiz</string>
    
    <!-- Welcome Screen -->
    <string name="welcome_title">AngoNurse Quiz</string>
    <string name="welcome_subtitle">Teste os seus conhecimentos em enfermagem</string>
    <string name="btn_start_quiz">Iniciar Quiz</string>
    <string name="btn_memory_game">Jogo da Memória</string>
    <string name="btn_about">Sobre o Projeto</string>
    <string name="btn_settings">Configurações</string>
    
    <!-- Features -->
    <string name="feature_questions">45 perguntas desafiadoras</string>
    <string name="feature_timer">Tempo limitado por questão</string>
    <string name="feature_score">Sistema de pontuação</string>
    
    <!-- Quiz Screen -->
    <string name="question_label">Pergunta %1$d de %2$d</string>
    <string name="time_remaining">Tempo restante</string>
    <string name="btn_next">Próxima</string>
    <string name="btn_finish">Terminar</string>
    <string name="btn_confirm">Confirmar</string>
    <string name="time_up">Tempo Esgotado!</string>
    <string name="time_up_message">O tempo para responder acabou.</string>
    
    <!-- Memory Game -->
    <string name="memory_title">Jogo da Memória</string>
    <string name="select_difficulty">Selecionar Dificuldade</string>
    <string name="difficulty_easy">Fácil</string>
    <string name="difficulty_medium">Médio</string>
    <string name="difficulty_hard">Difícil</string>
    <string name="difficulty_power">Power</string>
    <string name="pairs_found">Pares: %1$d/%2$d</string>
    <string name="moves_count">Movimentos: %1$d</string>
    
    <!-- Results Screen -->
    <string name="result_title">Resultado</string>
    <string name="your_score">A sua pontuação</string>
    <string name="correct_answers">Respostas Correctas</string>
    <string name="wrong_answers">Respostas Erradas</string>
    <string name="percentage">%1$d%%</string>
    <string name="btn_try_again">Tentar Novamente</string>
    <string name="btn_review">Rever Respostas</string>
    <string name="btn_home">Início</string>
    
    <!-- Performance Messages -->
    <string name="performance_excellent">Excelente! Você é um especialista!</string>
    <string name="performance_good">Muito Bem! Continue assim!</string>
    <string name="performance_average">Bom trabalho! Pode melhorar!</string>
    <string name="performance_poor">Continue estudando!</string>
    
    <!-- Memory Results -->
    <string name="memory_complete">Parabéns!</string>
    <string name="memory_time">Tempo: %1$s</string>
    <string name="memory_moves">Movimentos: %1$d</string>
    
    <!-- About Screen -->
    <string name="about_title">Sobre o Projeto</string>
    <string name="about_description">AngoNurse Quiz é uma aplicação educacional desenvolvida para ajudar estudantes e profissionais de enfermagem a testar e melhorar os seus conhecimentos.</string>
    <string name="about_version">Versão 1.0.0</string>
    <string name="about_developer">Desenvolvido por AngoNurse</string>
    <string name="btn_follow_facebook">Seguir no Facebook</string>
    
    <!-- Settings Screen -->
    <string name="settings_title">Configurações</string>
    <string name="settings_music">Música de Fundo</string>
    <string name="settings_sound">Efeitos Sonoros</string>
    <string name="settings_vibration">Vibração</string>
    
    <!-- General -->
    <string name="loading">A carregar…</string>
    <string name="error">Erro</string>
    <string name="ok">OK</string>
    <string name="cancel">Cancelar</string>
</resources>
```

### styles.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <!-- Base Theme -->
    <style name="Theme.AngoNurseGame" parent="Theme.Material3.Dark.NoActionBar">
        <item name="colorPrimary">@color/primary</item>
        <item name="colorPrimaryDark">@color/primary_dark</item>
        <item name="colorAccent">@color/primary_light</item>
        <item name="android:windowBackground">@color/background</item>
        <item name="android:statusBarColor">@color/background</item>
        <item name="android:navigationBarColor">@color/background</item>
        <item name="android:windowLightStatusBar">false</item>
        <item name="android:forceDarkAllowed">false</item>
    </style>

    <!-- Splash Theme -->
    <style name="Theme.AngoNurseGame.Splash" parent="Theme.AngoNurseGame">
        <item name="android:windowBackground">@color/background</item>
    </style>

    <!-- Text Styles -->
    <style name="TextStyle.Title">
        <item name="android:textSize">32sp</item>
        <item name="android:textColor">@color/text_primary</item>
        <item name="android:fontFamily">sans-serif-medium</item>
        <item name="android:textStyle">bold</item>
    </style>

    <style name="TextStyle.Subtitle">
        <item name="android:textSize">18sp</item>
        <item name="android:textColor">@color/text_secondary</item>
        <item name="android:fontFamily">sans-serif</item>
    </style>

    <style name="TextStyle.Body">
        <item name="android:textSize">16sp</item>
        <item name="android:textColor">@color/text_primary</item>
        <item name="android:fontFamily">sans-serif</item>
    </style>

    <style name="TextStyle.Caption">
        <item name="android:textSize">14sp</item>
        <item name="android:textColor">@color/text_muted</item>
        <item name="android:fontFamily">sans-serif</item>
    </style>

    <!-- Button Styles -->
    <style name="ButtonStyle.Primary">
        <item name="android:background">@drawable/bg_button_primary</item>
        <item name="android:textColor">@color/background</item>
        <item name="android:textSize">16sp</item>
        <item name="android:fontFamily">sans-serif-medium</item>
        <item name="android:textAllCaps">false</item>
        <item name="android:paddingStart">24dp</item>
        <item name="android:paddingEnd">24dp</item>
        <item name="android:paddingTop">16dp</item>
        <item name="android:paddingBottom">16dp</item>
        <item name="android:gravity">center</item>
    </style>

    <style name="ButtonStyle.Secondary">
        <item name="android:background">@drawable/bg_button_secondary</item>
        <item name="android:textColor">@color/text_primary</item>
        <item name="android:textSize">16sp</item>
        <item name="android:fontFamily">sans-serif-medium</item>
        <item name="android:textAllCaps">false</item>
        <item name="android:paddingStart">24dp</item>
        <item name="android:paddingEnd">24dp</item>
        <item name="android:paddingTop">14dp</item>
        <item name="android:paddingBottom">14dp</item>
        <item name="android:gravity">center</item>
    </style>

    <!-- Card Styles -->
    <style name="CardStyle.Glass">
        <item name="android:background">@drawable/bg_glass_card</item>
        <item name="android:padding">16dp</item>
    </style>

    <!-- Option Styles -->
    <style name="OptionStyle">
        <item name="android:background">@drawable/bg_option_normal</item>
        <item name="android:textColor">@color/text_primary</item>
        <item name="android:textSize">15sp</item>
        <item name="android:padding">16dp</item>
        <item name="android:gravity">center_vertical</item>
    </style>
</resources>
```

### dimens.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <!-- Margins and Paddings -->
    <dimen name="spacing_xs">4dp</dimen>
    <dimen name="spacing_sm">8dp</dimen>
    <dimen name="spacing_md">16dp</dimen>
    <dimen name="spacing_lg">24dp</dimen>
    <dimen name="spacing_xl">32dp</dimen>
    <dimen name="spacing_xxl">48dp</dimen>
    
    <!-- Corner Radius -->
    <dimen name="radius_sm">8dp</dimen>
    <dimen name="radius_md">12dp</dimen>
    <dimen name="radius_lg">16dp</dimen>
    <dimen name="radius_xl">24dp</dimen>
    <dimen name="radius_full">999dp</dimen>
    
    <!-- Text Sizes -->
    <dimen name="text_xs">12sp</dimen>
    <dimen name="text_sm">14sp</dimen>
    <dimen name="text_md">16sp</dimen>
    <dimen name="text_lg">18sp</dimen>
    <dimen name="text_xl">24sp</dimen>
    <dimen name="text_2xl">32sp</dimen>
    <dimen name="text_3xl">40sp</dimen>
    
    <!-- Icon Sizes -->
    <dimen name="icon_sm">20dp</dimen>
    <dimen name="icon_md">24dp</dimen>
    <dimen name="icon_lg">32dp</dimen>
    <dimen name="icon_xl">48dp</dimen>
    
    <!-- Button Height -->
    <dimen name="button_height">52dp</dimen>
    <dimen name="button_height_sm">44dp</dimen>
    
    <!-- Card dimensions -->
    <dimen name="card_elevation">4dp</dimen>
    
    <!-- Progress bar -->
    <dimen name="progress_height">6dp</dimen>
    
    <!-- Memory card -->
    <dimen name="memory_card_min_size">60dp</dimen>
</resources>
```

---

## 🎨 Drawables

### bg_gradient_dark.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <gradient
        android:type="linear"
        android:angle="135"
        android:startColor="@color/gradient_start"
        android:centerColor="@color/gradient_middle"
        android:endColor="@color/gradient_end" />
</shape>
```

### bg_glass_card.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <solid android:color="@color/glass_bg" />
    <corners android:radius="@dimen/radius_lg" />
    <stroke
        android:width="1dp"
        android:color="@color/glass_border" />
</shape>
```

### bg_button_primary.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<ripple xmlns:android="http://schemas.android.com/apk/res/android"
    android:color="@color/primary_dark">
    <item>
        <shape android:shape="rectangle">
            <solid android:color="@color/primary" />
            <corners android:radius="@dimen/radius_md" />
        </shape>
    </item>
</ripple>
```

### bg_button_secondary.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<ripple xmlns:android="http://schemas.android.com/apk/res/android"
    android:color="@color/surface_elevated">
    <item>
        <shape android:shape="rectangle">
            <solid android:color="@color/surface" />
            <corners android:radius="@dimen/radius_md" />
            <stroke
                android:width="1dp"
                android:color="@color/card_border" />
        </shape>
    </item>
</ripple>
```

### bg_option_normal.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<ripple xmlns:android="http://schemas.android.com/apk/res/android"
    android:color="@color/primary">
    <item>
        <shape android:shape="rectangle">
            <solid android:color="@color/option_normal" />
            <corners android:radius="@dimen/radius_md" />
            <stroke
                android:width="1dp"
                android:color="@color/card_border" />
        </shape>
    </item>
</ripple>
```

### bg_option_selected.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <solid android:color="@color/option_selected" />
    <corners android:radius="@dimen/radius_md" />
    <stroke
        android:width="2dp"
        android:color="@color/primary" />
</shape>
```

### bg_option_correct.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <solid android:color="@color/success_bg" />
    <corners android:radius="@dimen/radius_md" />
    <stroke
        android:width="2dp"
        android:color="@color/success" />
</shape>
```

### bg_option_wrong.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <solid android:color="@color/error_bg" />
    <corners android:radius="@dimen/radius_md" />
    <stroke
        android:width="2dp"
        android:color="@color/error" />
</shape>
```

### bg_memory_card.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<ripple xmlns:android="http://schemas.android.com/apk/res/android"
    android:color="@color/primary">
    <item>
        <shape android:shape="rectangle">
            <solid android:color="@color/memory_card_back" />
            <corners android:radius="@dimen/radius_md" />
            <stroke
                android:width="2dp"
                android:color="@color/primary" />
        </shape>
    </item>
</ripple>
```

### bg_memory_card_flipped.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <solid android:color="@color/memory_card_front" />
    <corners android:radius="@dimen/radius_md" />
    <stroke
        android:width="1dp"
        android:color="@color/card_border" />
</shape>
```

### bg_progress_bar.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:id="@android:id/background">
        <shape android:shape="rectangle">
            <solid android:color="@color/surface" />
            <corners android:radius="@dimen/radius_full" />
        </shape>
    </item>
    <item android:id="@android:id/progress">
        <clip>
            <shape android:shape="rectangle">
                <solid android:color="@color/primary" />
                <corners android:radius="@dimen/radius_full" />
            </shape>
        </clip>
    </item>
</layer-list>
```

### bg_timer.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <solid android:color="@color/glass_bg" />
    <corners android:radius="@dimen/radius_lg" />
    <stroke
        android:width="1dp"
        android:color="@color/glass_border" />
</shape>
```

---

## 📐 Layouts

### activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg_gradient_dark">

    <ImageView
        android:id="@+id/logoImage"
        android:layout_width="120dp"
        android:layout_height="120dp"
        android:src="@mipmap/ic_launcher"
        android:contentDescription="@string/app_name"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <ProgressBar
        android:id="@+id/progressBar"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="24dp"
        android:indeterminateTint="@color/primary"
        app:layout_constraintTop_toBottomOf="@id/logoImage"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### activity_welcome.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg_gradient_dark"
    android:fitsSystemWindows="true">

    <!-- Decorative circles -->
    <View
        android:id="@+id/decorCircle1"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:alpha="0.1"
        android:background="@drawable/bg_button_primary"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:translationX="50dp"
        android:translationY="-50dp" />

    <View
        android:id="@+id/decorCircle2"
        android:layout_width="150dp"
        android:layout_height="150dp"
        android:alpha="0.1"
        android:background="@drawable/bg_button_primary"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        android:translationX="-30dp"
        android:translationY="30dp" />

    <!-- Content Container - uses chain to distribute space -->
    <androidx.constraintlayout.widget.ConstraintLayout
        android:id="@+id/contentContainer"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:padding="@dimen/spacing_lg"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <!-- Top Section: Logo, Title, Subtitle, Features -->
        <LinearLayout
            android:id="@+id/topSection"
            android:layout_width="0dp"
            android:layout_height="0dp"
            android:orientation="vertical"
            android:gravity="center_horizontal"
            app:layout_constraintTop_toTopOf="parent"
            app:layout_constraintBottom_toTopOf="@id/buttonsContainer"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintVertical_weight="1">

            <!-- Logo -->
            <ImageView
                android:id="@+id/logoImage"
                android:layout_width="100dp"
                android:layout_height="100dp"
                android:layout_marginTop="@dimen/spacing_md"
                android:src="@mipmap/ic_launcher"
                android:contentDescription="@string/app_name" />

            <!-- Title -->
            <TextView
                android:id="@+id/titleText"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@string/welcome_title"
                style="@style/TextStyle.Title"
                android:layout_marginTop="@dimen/spacing_md" />

            <!-- Subtitle -->
            <TextView
                android:id="@+id/subtitleText"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="@string/welcome_subtitle"
                style="@style/TextStyle.Subtitle"
                android:textAlignment="center"
                android:layout_marginTop="@dimen/spacing_sm"
                android:layout_marginHorizontal="@dimen/spacing_lg" />

            <!-- Features Card -->
            <LinearLayout
                android:id="@+id/featuresCard"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="vertical"
                android:background="@drawable/bg_glass_card"
                android:padding="@dimen/spacing_md"
                android:layout_marginTop="@dimen/spacing_lg">

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="✓ 45 perguntas desafiadoras"
                    style="@style/TextStyle.Caption"
                    android:textColor="@color/text_secondary"
                    android:drawablePadding="@dimen/spacing_sm" />

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="✓ Tempo limitado por questão"
                    style="@style/TextStyle.Caption"
                    android:textColor="@color/text_secondary"
                    android:layout_marginTop="@dimen/spacing_xs" />

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="✓ Sistema de pontuação"
                    style="@style/TextStyle.Caption"
                    android:textColor="@color/text_secondary"
                    android:layout_marginTop="@dimen/spacing_xs" />

            </LinearLayout>

        </LinearLayout>

        <!-- Buttons Container - Fixed at bottom -->
        <LinearLayout
            android:id="@+id/buttonsContainer"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:layout_marginBottom="@dimen/spacing_sm"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintEnd_toEndOf="parent">

            <Button
                android:id="@+id/btnStartQuiz"
                android:layout_width="match_parent"
                android:layout_height="@dimen/button_height"
                android:text="@string/btn_start_quiz"
                style="@style/ButtonStyle.Primary" />

            <Button
                android:id="@+id/btnMemoryGame"
                android:layout_width="match_parent"
                android:layout_height="@dimen/button_height"
                android:text="@string/btn_memory_game"
                style="@style/ButtonStyle.Primary"
                android:layout_marginTop="@dimen/spacing_sm" />

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="horizontal"
                android:layout_marginTop="@dimen/spacing_sm"
                android:baselineAligned="false">

                <Button
                    android:id="@+id/btnAbout"
                    android:layout_width="0dp"
                    android:layout_height="@dimen/button_height_sm"
                    android:layout_weight="1"
                    android:layout_marginEnd="@dimen/spacing_xs"
                    android:text="@string/btn_about"
                    style="@style/ButtonStyle.Secondary" />

                <Button
                    android:id="@+id/btnSettings"
                    android:layout_width="0dp"
                    android:layout_height="@dimen/button_height_sm"
                    android:layout_weight="1"
                    android:layout_marginStart="@dimen/spacing_xs"
                    android:text="@string/btn_settings"
                    style="@style/ButtonStyle.Secondary" />

            </LinearLayout>

        </LinearLayout>

    </androidx.constraintlayout.widget.ConstraintLayout>

</androidx.constraintlayout.widget.ConstraintLayout>
```

### activity_quiz.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg_gradient_dark">

    <!-- Timer Card -->
    <LinearLayout
        android:id="@+id/timerCard"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:background="@drawable/bg_timer"
        android:padding="@dimen/spacing_md"
        android:layout_margin="@dimen/spacing_md"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:gravity="center_vertical">

            <ImageView
                android:id="@+id/timerIcon"
                android:layout_width="@dimen/icon_md"
                android:layout_height="@dimen/icon_md"
                android:src="@android:drawable/ic_menu_recent_history"
                android:tint="@color/primary"
                android:contentDescription="@string/time_remaining" />

            <TextView
                android:id="@+id/timerText"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="02:00"
                android:textSize="@dimen/text_xl"
                android:textColor="@color/text_primary"
                android:fontFamily="sans-serif-medium"
                android:layout_marginStart="@dimen/spacing_sm" />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@string/time_remaining"
                android:textSize="@dimen/text_sm"
                android:textColor="@color/text_muted"
                android:layout_marginStart="@dimen/spacing_sm" />

        </LinearLayout>

        <ProgressBar
            android:id="@+id/timerProgress"
            style="@android:style/Widget.ProgressBar.Horizontal"
            android:layout_width="match_parent"
            android:layout_height="@dimen/progress_height"
            android:layout_marginTop="@dimen/spacing_sm"
            android:progressDrawable="@drawable/bg_progress_bar"
            android:max="100"
            android:progress="100" />

    </LinearLayout>

    <!-- Question Progress -->
    <TextView
        android:id="@+id/questionProgress"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Pergunta 1 de 45"
        style="@style/TextStyle.Caption"
        android:layout_marginTop="@dimen/spacing_md"
        app:layout_constraintTop_toBottomOf="@id/timerCard"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <!-- Overall Progress Bar -->
    <ProgressBar
        android:id="@+id/overallProgress"
        style="@android:style/Widget.ProgressBar.Horizontal"
        android:layout_width="0dp"
        android:layout_height="4dp"
        android:layout_marginTop="@dimen/spacing_sm"
        android:layout_marginHorizontal="@dimen/spacing_md"
        android:progressDrawable="@drawable/bg_progress_bar"
        android:max="100"
        android:progress="0"
        app:layout_constraintTop_toBottomOf="@id/questionProgress"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <!-- Question Card -->
    <androidx.cardview.widget.CardView
        android:id="@+id/questionCard"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:layout_margin="@dimen/spacing_md"
        app:cardBackgroundColor="@color/card_bg"
        app:cardCornerRadius="@dimen/radius_lg"
        app:cardElevation="0dp"
        app:layout_constraintTop_toBottomOf="@id/overallProgress"
        app:layout_constraintBottom_toTopOf="@id/btnConfirm"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:orientation="vertical"
            android:padding="@dimen/spacing_md">

            <!-- Question Text - takes only needed space -->
            <TextView
                android:id="@+id/questionText"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="Qual é a pergunta?"
                android:textSize="@dimen/text_lg"
                android:textColor="@color/text_primary"
                android:fontFamily="sans-serif-medium"
                android:maxLines="4"
                android:ellipsize="end" />

            <!-- Options RecyclerView - fills remaining space -->
            <androidx.recyclerview.widget.RecyclerView
                android:id="@+id/optionsRecyclerView"
                android:layout_width="match_parent"
                android:layout_height="0dp"
                android:layout_weight="1"
                android:layout_marginTop="@dimen/spacing_md"
                android:clipToPadding="false"
                android:overScrollMode="never" />

        </LinearLayout>

    </androidx.cardview.widget.CardView>

    <!-- Confirm Button -->
    <Button
        android:id="@+id/btnConfirm"
        android:layout_width="0dp"
        android:layout_height="@dimen/button_height"
        android:layout_margin="@dimen/spacing_md"
        android:text="@string/btn_confirm"
        style="@style/ButtonStyle.Primary"
        android:enabled="false"
        android:alpha="0.5"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### activity_memory_game.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg_gradient_dark">

    <!-- Header -->
    <LinearLayout
        android:id="@+id/header"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:gravity="center_vertical"
        android:padding="@dimen/spacing_md"
        android:background="@drawable/bg_glass_card"
        android:layout_margin="@dimen/spacing_md"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <!-- Timer -->
        <LinearLayout
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:orientation="vertical">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Tempo"
                style="@style/TextStyle.Caption" />

            <TextView
                android:id="@+id/timerText"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="00:00"
                android:textSize="@dimen/text_lg"
                android:textColor="@color/primary"
                android:fontFamily="sans-serif-medium" />

        </LinearLayout>

        <!-- Pairs -->
        <LinearLayout
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:orientation="vertical"
            android:gravity="center">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Pares"
                style="@style/TextStyle.Caption" />

            <TextView
                android:id="@+id/pairsText"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="0/6"
                android:textSize="@dimen/text_lg"
                android:textColor="@color/success"
                android:fontFamily="sans-serif-medium" />

        </LinearLayout>

        <!-- Moves -->
        <LinearLayout
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:orientation="vertical"
            android:gravity="end">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Movimentos"
                style="@style/TextStyle.Caption" />

            <TextView
                android:id="@+id/movesText"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="0"
                android:textSize="@dimen/text_lg"
                android:textColor="@color/warning"
                android:fontFamily="sans-serif-medium" />

        </LinearLayout>

    </LinearLayout>

    <!-- Cards Grid - fills all available space -->
    <androidx.recyclerview.widget.RecyclerView
        android:id="@+id/cardsRecyclerView"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:layout_margin="@dimen/spacing_md"
        android:clipToPadding="false"
        android:overScrollMode="never"
        app:layout_constraintTop_toBottomOf="@id/header"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### activity_result.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg_gradient_dark"
    android:padding="@dimen/spacing_lg">

    <!-- Trophy Icon -->
    <TextView
        android:id="@+id/trophyIcon"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="🏆"
        android:textSize="64sp"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="@dimen/spacing_xl" />

    <!-- Performance Message -->
    <TextView
        android:id="@+id/performanceMessage"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/performance_excellent"
        style="@style/TextStyle.Title"
        android:textSize="@dimen/text_xl"
        android:textAlignment="center"
        android:layout_marginTop="@dimen/spacing_md"
        app:layout_constraintTop_toBottomOf="@id/trophyIcon"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <!-- Score Card -->
    <LinearLayout
        android:id="@+id/scoreCard"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:background="@drawable/bg_glass_card"
        android:padding="@dimen/spacing_lg"
        android:gravity="center"
        android:layout_marginTop="@dimen/spacing_lg"
        app:layout_constraintTop_toBottomOf="@id/performanceMessage"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <TextView
            android:id="@+id/percentageText"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="85%"
            android:textSize="@dimen/text_3xl"
            android:textColor="@color/primary"
            android:fontFamily="sans-serif-black" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/your_score"
            style="@style/TextStyle.Caption"
            android:layout_marginTop="@dimen/spacing_xs" />

    </LinearLayout>

    <!-- Stats Row -->
    <LinearLayout
        android:id="@+id/statsRow"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginTop="@dimen/spacing_md"
        app:layout_constraintTop_toBottomOf="@id/scoreCard"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <!-- Correct Answers -->
        <LinearLayout
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:orientation="vertical"
            android:background="@drawable/bg_glass_card"
            android:padding="@dimen/spacing_md"
            android:gravity="center"
            android:layout_marginEnd="@dimen/spacing_sm">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="✓"
                android:textSize="24sp"
                android:textColor="@color/success" />

            <TextView
                android:id="@+id/correctCount"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="38"
                android:textSize="@dimen/text_xl"
                android:textColor="@color/success"
                android:fontFamily="sans-serif-medium" />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@string/correct_answers"
                style="@style/TextStyle.Caption"
                android:textSize="11sp" />

        </LinearLayout>

        <!-- Wrong Answers -->
        <LinearLayout
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:orientation="vertical"
            android:background="@drawable/bg_glass_card"
            android:padding="@dimen/spacing_md"
            android:gravity="center"
            android:layout_marginStart="@dimen/spacing_sm">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="✗"
                android:textSize="24sp"
                android:textColor="@color/error" />

            <TextView
                android:id="@+id/wrongCount"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="7"
                android:textSize="@dimen/text_xl"
                android:textColor="@color/error"
                android:fontFamily="sans-serif-medium" />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@string/wrong_answers"
                style="@style/TextStyle.Caption"
                android:textSize="11sp" />

        </LinearLayout>

    </LinearLayout>

    <!-- Buttons -->
    <LinearLayout
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <Button
            android:id="@+id/btnReview"
            android:layout_width="match_parent"
            android:layout_height="@dimen/button_height"
            android:text="@string/btn_review"
            style="@style/ButtonStyle.Secondary" />

        <Button
            android:id="@+id/btnTryAgain"
            android:layout_width="match_parent"
            android:layout_height="@dimen/button_height"
            android:text="@string/btn_try_again"
            style="@style/ButtonStyle.Primary"
            android:layout_marginTop="@dimen/spacing_sm" />

        <Button
            android:id="@+id/btnHome"
            android:layout_width="match_parent"
            android:layout_height="@dimen/button_height_sm"
            android:text="@string/btn_home"
            style="@style/ButtonStyle.Secondary"
            android:layout_marginTop="@dimen/spacing_sm" />

    </LinearLayout>

</androidx.constraintlayout.widget.ConstraintLayout>
```

### activity_memory_result.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg_gradient_dark"
    android:padding="@dimen/spacing_lg">

    <!-- Celebration -->
    <TextView
        android:id="@+id/celebrationIcon"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="🎉"
        android:textSize="80sp"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintBottom_toTopOf="@id/congratsText"
        app:layout_constraintVertical_chainStyle="packed" />

    <TextView
        android:id="@+id/congratsText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/memory_complete"
        style="@style/TextStyle.Title"
        android:layout_marginTop="@dimen/spacing_md"
        app:layout_constraintTop_toBottomOf="@id/celebrationIcon"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintBottom_toTopOf="@id/statsCard" />

    <!-- Stats Card -->
    <LinearLayout
        android:id="@+id/statsCard"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginTop="@dimen/spacing_xl"
        app:layout_constraintTop_toBottomOf="@id/congratsText"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintBottom_toTopOf="@id/btnPlayAgain">

        <!-- Time -->
        <LinearLayout
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:orientation="vertical"
            android:background="@drawable/bg_glass_card"
            android:padding="@dimen/spacing_lg"
            android:gravity="center"
            android:layout_marginEnd="@dimen/spacing_sm">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="⏱️"
                android:textSize="32sp" />

            <TextView
                android:id="@+id/timeText"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="01:23"
                android:textSize="@dimen/text_xl"
                android:textColor="@color/primary"
                android:fontFamily="sans-serif-medium"
                android:layout_marginTop="@dimen/spacing_sm" />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Tempo"
                style="@style/TextStyle.Caption" />

        </LinearLayout>

        <!-- Moves -->
        <LinearLayout
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:orientation="vertical"
            android:background="@drawable/bg_glass_card"
            android:padding="@dimen/spacing_lg"
            android:gravity="center"
            android:layout_marginStart="@dimen/spacing_sm">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="🎯"
                android:textSize="32sp" />

            <TextView
                android:id="@+id/movesText"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="24"
                android:textSize="@dimen/text_xl"
                android:textColor="@color/warning"
                android:fontFamily="sans-serif-medium"
                android:layout_marginTop="@dimen/spacing_sm" />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Movimentos"
                style="@style/TextStyle.Caption" />

        </LinearLayout>

    </LinearLayout>

    <!-- Buttons -->
    <Button
        android:id="@+id/btnPlayAgain"
        android:layout_width="0dp"
        android:layout_height="@dimen/button_height"
        android:text="Jogar Novamente"
        style="@style/ButtonStyle.Primary"
        android:layout_marginBottom="@dimen/spacing_sm"
        app:layout_constraintBottom_toTopOf="@id/btnHome"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <Button
        android:id="@+id/btnHome"
        android:layout_width="0dp"
        android:layout_height="@dimen/button_height_sm"
        android:text="@string/btn_home"
        style="@style/ButtonStyle.Secondary"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### activity_about.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg_gradient_dark"
    android:padding="@dimen/spacing_lg">

    <!-- Back Button -->
    <ImageButton
        android:id="@+id/btnBack"
        android:layout_width="48dp"
        android:layout_height="48dp"
        android:background="@drawable/bg_button_secondary"
        android:src="@android:drawable/ic_menu_revert"
        android:tint="@color/text_primary"
        android:contentDescription="Voltar"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

    <!-- Logo -->
    <ImageView
        android:id="@+id/logoImage"
        android:layout_width="120dp"
        android:layout_height="120dp"
        android:src="@mipmap/ic_launcher"
        android:contentDescription="@string/app_name"
        android:layout_marginTop="@dimen/spacing_xl"
        app:layout_constraintTop_toBottomOf="@id/btnBack"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <!-- Title -->
    <TextView
        android:id="@+id/titleText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/about_title"
        style="@style/TextStyle.Title"
        android:layout_marginTop="@dimen/spacing_md"
        app:layout_constraintTop_toBottomOf="@id/logoImage"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <!-- Description Card -->
    <LinearLayout
        android:id="@+id/descriptionCard"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:background="@drawable/bg_glass_card"
        android:padding="@dimen/spacing_lg"
        android:layout_marginTop="@dimen/spacing_lg"
        app:layout_constraintTop_toBottomOf="@id/titleText"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="@string/about_description"
            style="@style/TextStyle.Body"
            android:textAlignment="center"
            android:lineSpacingMultiplier="1.4" />

        <View
            android:layout_width="60dp"
            android:layout_height="2dp"
            android:background="@color/primary"
            android:layout_gravity="center"
            android:layout_marginVertical="@dimen/spacing_md" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/about_version"
            style="@style/TextStyle.Caption"
            android:layout_gravity="center" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/about_developer"
            style="@style/TextStyle.Caption"
            android:layout_gravity="center"
            android:layout_marginTop="@dimen/spacing_xs" />

    </LinearLayout>

    <!-- Facebook Button -->
    <Button
        android:id="@+id/btnFacebook"
        android:layout_width="0dp"
        android:layout_height="@dimen/button_height"
        android:text="@string/btn_follow_facebook"
        style="@style/ButtonStyle.Primary"
        android:drawableStart="@android:drawable/ic_menu_share"
        android:drawablePadding="@dimen/spacing_sm"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### activity_settings.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg_gradient_dark"
    android:padding="@dimen/spacing_lg">

    <!-- Back Button -->
    <ImageButton
        android:id="@+id/btnBack"
        android:layout_width="48dp"
        android:layout_height="48dp"
        android:background="@drawable/bg_button_secondary"
        android:src="@android:drawable/ic_menu_revert"
        android:tint="@color/text_primary"
        android:contentDescription="Voltar"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

    <!-- Title -->
    <TextView
        android:id="@+id/titleText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/settings_title"
        style="@style/TextStyle.Title"
        app:layout_constraintTop_toTopOf="@id/btnBack"
        app:layout_constraintBottom_toBottomOf="@id/btnBack"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <!-- Settings Card -->
    <LinearLayout
        android:id="@+id/settingsCard"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:background="@drawable/bg_glass_card"
        android:padding="@dimen/spacing_md"
        android:layout_marginTop="@dimen/spacing_xl"
        app:layout_constraintTop_toBottomOf="@id/btnBack"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <!-- Music Toggle -->
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:gravity="center_vertical"
            android:padding="@dimen/spacing_sm">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="🎵"
                android:textSize="24sp" />

            <LinearLayout
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:orientation="vertical"
                android:layout_marginStart="@dimen/spacing_md">

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="@string/settings_music"
                    style="@style/TextStyle.Body" />

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="Música de fundo durante o jogo"
                    style="@style/TextStyle.Caption" />

            </LinearLayout>

            <com.google.android.material.switchmaterial.SwitchMaterial
                android:id="@+id/switchMusic"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:thumbTint="@color/primary"
                android:trackTint="@color/surface_elevated" />

        </LinearLayout>

        <View
            android:layout_width="match_parent"
            android:layout_height="1dp"
            android:background="@color/card_border"
            android:layout_marginVertical="@dimen/spacing_sm" />

        <!-- Sound Effects Toggle -->
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:gravity="center_vertical"
            android:padding="@dimen/spacing_sm">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="🔊"
                android:textSize="24sp" />

            <LinearLayout
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:orientation="vertical"
                android:layout_marginStart="@dimen/spacing_md">

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="@string/settings_sound"
                    style="@style/TextStyle.Body" />

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="Sons ao acertar e errar"
                    style="@style/TextStyle.Caption" />

            </LinearLayout>

            <com.google.android.material.switchmaterial.SwitchMaterial
                android:id="@+id/switchSound"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:thumbTint="@color/primary"
                android:trackTint="@color/surface_elevated" />

        </LinearLayout>

        <View
            android:layout_width="match_parent"
            android:layout_height="1dp"
            android:background="@color/card_border"
            android:layout_marginVertical="@dimen/spacing_sm" />

        <!-- Vibration Toggle -->
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:gravity="center_vertical"
            android:padding="@dimen/spacing_sm">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="📳"
                android:textSize="24sp" />

            <LinearLayout
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:orientation="vertical"
                android:layout_marginStart="@dimen/spacing_md">

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="@string/settings_vibration"
                    style="@style/TextStyle.Body" />

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="Vibrar ao responder"
                    style="@style/TextStyle.Caption" />

            </LinearLayout>

            <com.google.android.material.switchmaterial.SwitchMaterial
                android:id="@+id/switchVibration"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:thumbTint="@color/primary"
                android:trackTint="@color/surface_elevated" />

        </LinearLayout>

    </LinearLayout>

</androidx.constraintlayout.widget.ConstraintLayout>
```

### item_quiz_option.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/optionContainer"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:minHeight="56dp"
    android:orientation="horizontal"
    android:gravity="center_vertical"
    android:background="@drawable/bg_option_normal"
    android:paddingHorizontal="@dimen/spacing_md"
    android:paddingVertical="@dimen/spacing_sm"
    android:layout_marginBottom="@dimen/spacing_sm"
    android:clickable="true"
    android:focusable="true">

    <TextView
        android:id="@+id/optionLetter"
        android:layout_width="36dp"
        android:layout_height="36dp"
        android:background="@drawable/bg_button_secondary"
        android:gravity="center"
        android:text="A"
        android:textColor="@color/primary"
        android:textSize="@dimen/text_md"
        android:fontFamily="sans-serif-medium"
        tools:ignore="HardcodedText" />

    <TextView
        android:id="@+id/optionText"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:layout_marginStart="@dimen/spacing_md"
        android:text="Opção de resposta"
        android:textColor="@color/text_primary"
        android:textSize="@dimen/text_sm"
        android:maxLines="4"
        android:ellipsize="end"
        tools:ignore="HardcodedText" />

</LinearLayout>
```

### item_memory_card.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/cardContainer"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:padding="4dp">

    <androidx.cardview.widget.CardView
        android:id="@+id/cardView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:cardBackgroundColor="@color/memory_card_back"
        app:cardCornerRadius="@dimen/radius_md"
        app:cardElevation="4dp"
        xmlns:app="http://schemas.android.com/apk/res-auto">

        <FrameLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent">

            <!-- Card Back (Question Mark) -->
            <TextView
                android:id="@+id/cardBack"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:gravity="center"
                android:text="?"
                android:textSize="28sp"
                android:textColor="@color/primary"
                android:fontFamily="sans-serif-black"
                android:visibility="visible" />

            <!-- Card Front (Image) -->
            <ImageView
                android:id="@+id/cardImage"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:padding="8dp"
                android:scaleType="fitCenter"
                android:visibility="gone"
                android:contentDescription="Card image" />

        </FrameLayout>

    </androidx.cardview.widget.CardView>

</FrameLayout>
```

### dialog_difficulty.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="vertical"
    android:background="@color/card_bg"
    android:padding="@dimen/spacing_lg">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/select_difficulty"
        style="@style/TextStyle.Title"
        android:textSize="@dimen/text_xl"
        android:layout_gravity="center" />

    <Button
        android:id="@+id/btnEasy"
        android:layout_width="match_parent"
        android:layout_height="@dimen/button_height"
        android:text="@string/difficulty_easy"
        style="@style/ButtonStyle.Secondary"
        android:layout_marginTop="@dimen/spacing_lg" />

    <Button
        android:id="@+id/btnMedium"
        android:layout_width="match_parent"
        android:layout_height="@dimen/button_height"
        android:text="@string/difficulty_medium"
        style="@style/ButtonStyle.Secondary"
        android:layout_marginTop="@dimen/spacing_sm" />

    <Button
        android:id="@+id/btnHard"
        android:layout_width="match_parent"
        android:layout_height="@dimen/button_height"
        android:text="@string/difficulty_hard"
        style="@style/ButtonStyle.Secondary"
        android:layout_marginTop="@dimen/spacing_sm" />

    <Button
        android:id="@+id/btnPower"
        android:layout_width="match_parent"
        android:layout_height="@dimen/button_height"
        android:text="@string/difficulty_power"
        style="@style/ButtonStyle.Primary"
        android:layout_marginTop="@dimen/spacing_sm" />

</LinearLayout>
```

---

## 📦 Models

### Question.kt

```kotlin
package com.angonurse.game2.models

data class Question(
    val id: Int,
    val text: String,
    val options: List<String>,
    val correctAnswer: String
) {
    // Retorna uma cópia com opções baralhadas
    fun withShuffledOptions(): Question {
        val shuffledOptions = options.shuffled()
        return this.copy(options = shuffledOptions)
    }
}
```

### MemoryCard.kt

```kotlin
package com.angonurse.game2.models

data class MemoryCard(
    val id: Int,
    val pairId: Int,
    val imageResId: Int,
    var isFlipped: Boolean = false,
    var isMatched: Boolean = false
)
```

### DifficultyLevel.kt

```kotlin
package com.angonurse.game2.models

enum class DifficultyLevel(
    val displayName: String,
    val pairsCount: Int,
    val columns: Int
) {
    EASY("Fácil", 4, 2),      // 8 cards = 4 pairs, 2 columns
    MEDIUM("Médio", 5, 2),    // 10 cards = 5 pairs, 2 columns
    HARD("Difícil", 6, 3),    // 12 cards = 6 pairs, 3 columns
    POWER("Power", 7, 4)      // 14 cards = 7 pairs, 4 columns
}
```

---

## 🎮 Managers

### QuizManager.kt

```kotlin
package com.angonurse.game2.managers

import com.angonurse.game2.models.Question

class QuizManager {
    
    private var questions: List<Question> = emptyList()
    private var currentIndex = 0
    private var userAnswers: MutableList<String> = mutableListOf()
    
    companion object {
        private const val TIME_PER_QUESTION = 120 // 2 minutos em segundos
        
        // 45 perguntas de enfermagem
        private val ALL_QUESTIONS = listOf(
            Question(1, "Qual é a via de administração mais rápida para um medicamento fazer efeito?", 
                listOf("Via oral", "Via intravenosa", "Via intramuscular", "Via subcutânea"), "Via intravenosa"),
            Question(2, "Qual é o principal objectivo da lavagem das mãos no ambiente hospitalar?", 
                listOf("Remover sujidade visível", "Prevenir infecções cruzadas", "Hidratar a pele", "Cumprir normas"), "Prevenir infecções cruzadas"),
            Question(3, "Qual é a posição indicada para um paciente com dificuldade respiratória?", 
                listOf("Decúbito dorsal", "Decúbito ventral", "Fowler", "Trendelenburg"), "Fowler"),
            Question(4, "Qual é o valor normal da pressão arterial em adultos?", 
                listOf("140/90 mmHg", "120/80 mmHg", "100/60 mmHg", "160/100 mmHg"), "120/80 mmHg"),
            Question(5, "Qual é a frequência cardíaca normal em adultos em repouso?", 
                listOf("40-60 bpm", "60-100 bpm", "100-120 bpm", "120-140 bpm"), "60-100 bpm"),
            Question(6, "Qual é o calibre de agulha mais indicado para administração intramuscular em adultos?", 
                listOf("18G", "21G", "25G", "30G"), "21G"),
            Question(7, "Qual é a temperatura corporal normal?", 
                listOf("35-36°C", "36-37.5°C", "38-39°C", "37.5-38°C"), "36-37.5°C"),
            Question(8, "Qual é o local mais indicado para verificar pulso em situação de emergência?", 
                listOf("Pulso radial", "Pulso carotídeo", "Pulso femoral", "Pulso braquial"), "Pulso carotídeo"),
            Question(9, "Quantas gotas correspondem a 1 ml em equipo macrogotas?", 
                listOf("10 gotas", "15 gotas", "20 gotas", "60 gotas"), "20 gotas"),
            Question(10, "Qual é a sequência correcta do BLS (Suporte Básico de Vida)?", 
                listOf("ABC", "CAB", "ACB", "BCA"), "CAB"),
            Question(11, "Qual é o ângulo correto para injeção intramuscular?", 
                listOf("15°", "45°", "90°", "180°"), "90°"),
            Question(12, "Qual é o tempo máximo de garroteamento para coleta de sangue?", 
                listOf("30 segundos", "1 minuto", "2 minutos", "5 minutos"), "1 minuto"),
            Question(13, "Qual é a frequência respiratória normal em adultos?", 
                listOf("8-12 irpm", "12-20 irpm", "20-30 irpm", "30-40 irpm"), "12-20 irpm"),
            Question(14, "Qual é o principal sinal de choque hipovolêmico?", 
                listOf("Hipertensão", "Bradicardia", "Hipotensão", "Febre"), "Hipotensão"),
            Question(15, "Qual é a via de administração da vacina BCG?", 
                listOf("Intramuscular", "Subcutânea", "Intradérmica", "Oral"), "Intradérmica"),
            Question(16, "Qual é o primeiro passo ao encontrar uma vítima inconsciente?", 
                listOf("Iniciar RCP", "Verificar responsividade", "Chamar ajuda", "Verificar pulso"), "Verificar responsividade"),
            Question(17, "Qual é a proporção de compressões/ventilações no RCP adulto?", 
                listOf("15:2", "30:2", "15:1", "30:1"), "30:2"),
            Question(18, "Qual é a profundidade correta das compressões torácicas em adultos?", 
                listOf("2-3 cm", "5-6 cm", "7-8 cm", "10 cm"), "5-6 cm"),
            Question(19, "Qual é o local correto para aplicação de insulina?", 
                listOf("Músculo deltóide", "Região abdominal", "Músculo glúteo", "Região dorsal"), "Região abdominal"),
            Question(20, "Qual é a definição de febre?", 
                listOf("Temperatura acima de 36°C", "Temperatura acima de 37°C", "Temperatura acima de 37.8°C", "Temperatura acima de 39°C"), "Temperatura acima de 37.8°C"),
            Question(21, "Qual é o tipo de precaução para paciente com tuberculose?", 
                listOf("Precaução de contato", "Precaução por gotículas", "Precaução por aerossóis", "Precaução padrão apenas"), "Precaução por aerossóis"),
            Question(22, "Qual é a ordem correta para realizar curativo?", 
                listOf("Limpeza, antissepsia, cobertura", "Antissepsia, limpeza, cobertura", "Cobertura, limpeza, antissepsia", "Limpeza, cobertura, antissepsia"), "Limpeza, antissepsia, cobertura"),
            Question(23, "Qual é o volume máximo para injeção intramuscular no deltóide?", 
                listOf("1 ml", "2 ml", "3 ml", "5 ml"), "2 ml"),
            Question(24, "Qual é a via de administração da vacina contra gripe?", 
                listOf("Intradérmica", "Subcutânea", "Intramuscular", "Oral"), "Intramuscular"),
            Question(25, "Qual é o primeiro sinal vital a alterar em caso de hemorragia?", 
                listOf("Pressão arterial", "Temperatura", "Frequência cardíaca", "Frequência respiratória"), "Frequência cardíaca"),
            Question(26, "Qual é a posição de Trendelenburg?", 
                listOf("Cabeça elevada", "Pés elevados", "Decúbito lateral", "Posição sentada"), "Pés elevados"),
            Question(27, "Qual é o objectivo principal da oxigenoterapia?", 
                listOf("Aquecer o paciente", "Corrigir hipoxemia", "Hidratar vias aéreas", "Facilitar respiração"), "Corrigir hipoxemia"),
            Question(28, "Qual é a saturação de oxigênio normal?", 
                listOf("85-90%", "90-94%", "95-100%", "100-105%"), "95-100%"),
            Question(29, "Qual é o tempo de troca de equipo de soro?", 
                listOf("12 horas", "24 horas", "48 horas", "72 horas"), "72 horas"),
            Question(30, "Qual é a escala utilizada para avaliar nível de consciência?", 
                listOf("Escala de Braden", "Escala de Glasgow", "Escala de Norton", "Escala de Morse"), "Escala de Glasgow"),
            Question(31, "Qual é a pontuação mínima na Escala de Glasgow?", 
                listOf("0", "1", "3", "5"), "3"),
            Question(32, "Qual é a função do enfermeiro na triagem?", 
                listOf("Diagnosticar doenças", "Classificar prioridade de atendimento", "Prescrever medicamentos", "Realizar cirurgias"), "Classificar prioridade de atendimento"),
            Question(33, "Qual é o tempo máximo para administração de sangue?", 
                listOf("2 horas", "4 horas", "6 horas", "8 horas"), "4 horas"),
            Question(34, "Qual é a diluição padrão de adrenalina para PCR?", 
                listOf("1:100", "1:1000", "1:10000", "1:100000"), "1:10000"),
            Question(35, "Qual é a posição para punção lombar?", 
                listOf("Decúbito dorsal", "Decúbito lateral com flexão", "Fowler", "Sentado"), "Decúbito lateral com flexão"),
            Question(36, "Qual é o sinal de Homans positivo indica?", 
                listOf("Apendicite", "Trombose venosa profunda", "Colecistite", "Pancreatite"), "Trombose venosa profunda"),
            Question(37, "Qual é o ritmo de compressões torácicas por minuto?", 
                listOf("60-80", "80-100", "100-120", "120-140"), "100-120"),
            Question(38, "Qual é a dose de adrenalina no PCR adulto?", 
                listOf("0.5 mg", "1 mg", "2 mg", "5 mg"), "1 mg"),
            Question(39, "Qual é a classificação de queimadura que atinge todas as camadas da pele?", 
                listOf("1º grau", "2º grau", "3º grau", "4º grau"), "3º grau"),
            Question(40, "Qual é o antídoto para intoxicação por benzodiazepínicos?", 
                listOf("Naloxona", "Flumazenil", "Atropina", "Glucagon"), "Flumazenil"),
            Question(41, "Qual é a técnica correta de aspiração de secreções?", 
                listOf("Introduzir aspirando", "Introduzir sem aspirar e retirar aspirando", "Aspirar continuamente", "Introduzir e retirar sem aspirar"), "Introduzir sem aspirar e retirar aspirando"),
            Question(42, "Qual é o tempo máximo de aspiração traqueal?", 
                listOf("5 segundos", "10 segundos", "15 segundos", "30 segundos"), "15 segundos"),
            Question(43, "Qual é a complicação mais comum da imobilidade prolongada?", 
                listOf("Hipertensão", "Úlcera por pressão", "Diabetes", "Asma"), "Úlcera por pressão"),
            Question(44, "Qual é a escala para avaliação de risco de úlcera por pressão?", 
                listOf("Glasgow", "Braden", "Apgar", "Morse"), "Braden"),
            Question(45, "Qual é o objectivo da mudança de decúbito?", 
                listOf("Facilitar alimentação", "Prevenir úlceras por pressão", "Melhorar comunicação", "Facilitar higiene"), "Prevenir úlceras por pressão")
        )
    }
    
    fun initQuiz() {
        // Baralha as perguntas e as opções de cada pergunta
        questions = ALL_QUESTIONS.shuffled().map { it.withShuffledOptions() }
        currentIndex = 0
        userAnswers.clear()
    }
    
    fun getCurrentQuestion(): Question? {
        return if (currentIndex < questions.size) questions[currentIndex] else null
    }
    
    fun getCurrentIndex(): Int = currentIndex
    
    fun getTotalQuestions(): Int = questions.size
    
    fun getTimePerQuestion(): Int = TIME_PER_QUESTION
    
    fun answerQuestion(answer: String): Boolean {
        val question = getCurrentQuestion() ?: return false
        userAnswers.add(answer)
        return answer == question.correctAnswer
    }
    
    fun nextQuestion(): Boolean {
        if (currentIndex < questions.size - 1) {
            currentIndex++
            return true
        }
        return false
    }
    
    fun isLastQuestion(): Boolean = currentIndex == questions.size - 1
    
    fun getScore(): Int {
        var score = 0
        for (i in userAnswers.indices) {
            if (i < questions.size && userAnswers[i] == questions[i].correctAnswer) {
                score++
            }
        }
        return score
    }
    
    fun getPercentage(): Int {
        return if (questions.isNotEmpty()) (getScore() * 100) / questions.size else 0
    }
    
    fun getQuestions(): List<Question> = questions
    
    fun getUserAnswers(): List<String> = userAnswers
    
    fun getCorrectCount(): Int = getScore()
    
    fun getWrongCount(): Int = questions.size - getScore()
}
```

### MemoryGameManager.kt

```kotlin
package com.angonurse.game2.managers

import com.angonurse.game2.models.DifficultyLevel
import com.angonurse.game2.models.MemoryCard

class MemoryGameManager(private val difficulty: DifficultyLevel) {
    
    private var cards: MutableList<MemoryCard> = mutableListOf()
    private var firstCard: MemoryCard? = null
    private var secondCard: MemoryCard? = null
    private var pairsFound = 0
    private var moves = 0
    private var isProcessing = false
    
    fun initGame(imageResIds: List<Int>) {
        cards.clear()
        pairsFound = 0
        moves = 0
        isProcessing = false
        firstCard = null
        secondCard = null
        
        // Seleciona imagens baseado na dificuldade
        val selectedImages = imageResIds.take(difficulty.pairsCount)
        
        var cardId = 0
        selectedImages.forEachIndexed { index, imageResId ->
            // Cria par de cartas
            cards.add(MemoryCard(cardId++, index, imageResId))
            cards.add(MemoryCard(cardId++, index, imageResId))
        }
        
        // Baralha as cartas
        cards.shuffle()
    }
    
    fun getCards(): List<MemoryCard> = cards
    
    fun getColumns(): Int = difficulty.columns
    
    fun getPairsCount(): Int = difficulty.pairsCount
    
    fun getPairsFound(): Int = pairsFound
    
    fun getMoves(): Int = moves
    
    fun isProcessing(): Boolean = isProcessing
    
    fun setProcessing(processing: Boolean) {
        isProcessing = processing
    }
    
    fun flipCard(position: Int): FlipResult {
        if (isProcessing) return FlipResult.PROCESSING
        
        val card = cards.getOrNull(position) ?: return FlipResult.INVALID
        
        if (card.isFlipped || card.isMatched) return FlipResult.ALREADY_FLIPPED
        
        card.isFlipped = true
        
        return when {
            firstCard == null -> {
                firstCard = card
                FlipResult.FIRST_CARD
            }
            secondCard == null -> {
                secondCard = card
                moves++
                FlipResult.SECOND_CARD
            }
            else -> FlipResult.PROCESSING
        }
    }
    
    fun checkMatch(): MatchResult {
        val first = firstCard ?: return MatchResult.NO_MATCH
        val second = secondCard ?: return MatchResult.NO_MATCH
        
        return if (first.pairId == second.pairId) {
            first.isMatched = true
            second.isMatched = true
            pairsFound++
            firstCard = null
            secondCard = null
            
            if (pairsFound == difficulty.pairsCount) {
                MatchResult.GAME_COMPLETE
            } else {
                MatchResult.MATCH
            }
        } else {
            MatchResult.NO_MATCH
        }
    }
    
    fun resetUnmatched() {
        firstCard?.isFlipped = false
        secondCard?.isFlipped = false
        firstCard = null
        secondCard = null
    }
    
    fun isGameComplete(): Boolean = pairsFound == difficulty.pairsCount
    
    enum class FlipResult {
        FIRST_CARD, SECOND_CARD, ALREADY_FLIPPED, PROCESSING, INVALID
    }
    
    enum class MatchResult {
        MATCH, NO_MATCH, GAME_COMPLETE
    }
}
```

### SoundManager.kt

```kotlin
package com.angonurse.game2.managers

import android.content.Context
import android.media.AudioAttributes
import android.media.MediaPlayer
import android.media.SoundPool
import com.angonurse.game2.R

class SoundManager(private val context: Context) {
    
    private var soundPool: SoundPool? = null
    private var matchSoundId: Int = 0
    private var mismatchSoundId: Int = 0
    private var mediaPlayer: MediaPlayer? = null
    private var isSoundEnabled = true
    private var isMusicEnabled = false
    
    init {
        val audioAttributes = AudioAttributes.Builder()
            .setUsage(AudioAttributes.USAGE_GAME)
            .setContentType(AudioAttributes.CONTENT_TYPE_SONIFICATION)
            .build()
        
        soundPool = SoundPool.Builder()
            .setMaxStreams(4)
            .setAudioAttributes(audioAttributes)
            .build()
        
        // Carrega os sons
        matchSoundId = soundPool?.load(context, R.raw.sound_match, 1) ?: 0
        mismatchSoundId = soundPool?.load(context, R.raw.sound_mismatch, 1) ?: 0
    }
    
    fun playMatch() {
        if (isSoundEnabled && matchSoundId != 0) {
            soundPool?.play(matchSoundId, 1f, 1f, 1, 0, 1f)
        }
    }
    
    fun playMismatch() {
        if (isSoundEnabled && mismatchSoundId != 0) {
            soundPool?.play(mismatchSoundId, 1f, 1f, 1, 0, 1f)
        }
    }
    
    fun startBackgroundMusic() {
        if (!isMusicEnabled) return
        
        try {
            if (mediaPlayer == null) {
                mediaPlayer = MediaPlayer.create(context, R.raw.musica)
                mediaPlayer?.isLooping = true
            }
            mediaPlayer?.start()
        } catch (e: Exception) {
            e.printStackTrace()
        }
    }
    
    fun stopBackgroundMusic() {
        try {
            mediaPlayer?.pause()
        } catch (e: Exception) {
            e.printStackTrace()
        }
    }
    
    fun setSoundEnabled(enabled: Boolean) {
        isSoundEnabled = enabled
    }
    
    fun setMusicEnabled(enabled: Boolean) {
        isMusicEnabled = enabled
        if (enabled) {
            startBackgroundMusic()
        } else {
            stopBackgroundMusic()
        }
    }
    
    fun isSoundEnabled(): Boolean = isSoundEnabled
    
    fun isMusicEnabled(): Boolean = isMusicEnabled
    
    fun release() {
        soundPool?.release()
        soundPool = null
        mediaPlayer?.release()
        mediaPlayer = null
    }
}
```

---

## 🔧 Utils

### PreferencesHelper.kt

```kotlin
package com.angonurse.game2.utils

import android.content.Context
import android.content.SharedPreferences

class PreferencesHelper(context: Context) {
    
    companion object {
        private const val PREFS_NAME = "angonurse_prefs"
        private const val KEY_MUSIC_ENABLED = "music_enabled"
        private const val KEY_SOUND_ENABLED = "sound_enabled"
        private const val KEY_VIBRATION_ENABLED = "vibration_enabled"
    }
    
    private val prefs: SharedPreferences = 
        context.getSharedPreferences(PREFS_NAME, Context.MODE_PRIVATE)
    
    var isMusicEnabled: Boolean
        get() = prefs.getBoolean(KEY_MUSIC_ENABLED, false)
        set(value) = prefs.edit().putBoolean(KEY_MUSIC_ENABLED, value).apply()
    
    var isSoundEnabled: Boolean
        get() = prefs.getBoolean(KEY_SOUND_ENABLED, true)
        set(value) = prefs.edit().putBoolean(KEY_SOUND_ENABLED, value).apply()
    
    var isVibrationEnabled: Boolean
        get() = prefs.getBoolean(KEY_VIBRATION_ENABLED, true)
        set(value) = prefs.edit().putBoolean(KEY_VIBRATION_ENABLED, value).apply()
}
```

### ScreenUtils.kt

```kotlin
package com.angonurse.game2.utils

import android.content.Context
import android.util.DisplayMetrics

object ScreenUtils {
    
    fun getScreenWidth(context: Context): Int {
        val displayMetrics = context.resources.displayMetrics
        return displayMetrics.widthPixels
    }
    
    fun getScreenHeight(context: Context): Int {
        val displayMetrics = context.resources.displayMetrics
        return displayMetrics.heightPixels
    }
    
    fun dpToPx(context: Context, dp: Float): Int {
        val density = context.resources.displayMetrics.density
        return (dp * density).toInt()
    }
    
    fun pxToDp(context: Context, px: Int): Float {
        val density = context.resources.displayMetrics.density
        return px / density
    }
    
    fun calculateCardSize(context: Context, columns: Int, totalCards: Int, availableHeight: Int): Int {
        val screenWidth = getScreenWidth(context)
        val horizontalPadding = dpToPx(context, 32f) // 16dp each side
        val cardSpacing = dpToPx(context, 8f) * (columns - 1)
        val availableWidth = screenWidth - horizontalPadding - cardSpacing
        
        val cardWidth = availableWidth / columns
        
        // Calculate rows needed
        val rows = (totalCards + columns - 1) / columns
        val verticalSpacing = dpToPx(context, 8f) * (rows - 1)
        val availableCardHeight = (availableHeight - verticalSpacing) / rows
        
        // Return the smaller dimension to ensure cards fit
        return minOf(cardWidth, availableCardHeight)
    }
}
```

---

## 📱 Adapters

### QuizOptionAdapter.kt

```kotlin
package com.angonurse.game2.adapters

import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.LinearLayout
import android.widget.TextView
import androidx.recyclerview.widget.RecyclerView
import com.angonurse.game2.R

class QuizOptionAdapter(
    private var options: List<String>,
    private val onOptionSelected: (Int, String) -> Unit
) : RecyclerView.Adapter<QuizOptionAdapter.OptionViewHolder>() {
    
    private var selectedPosition: Int = -1
    private var correctPosition: Int = -1
    private var showResult: Boolean = false
    
    inner class OptionViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) {
        val container: LinearLayout = itemView.findViewById(R.id.optionContainer)
        val letterText: TextView = itemView.findViewById(R.id.optionLetter)
        val optionText: TextView = itemView.findViewById(R.id.optionText)
        
        init {
            container.setOnClickListener {
                if (!showResult && adapterPosition != RecyclerView.NO_POSITION) {
                    val previousSelected = selectedPosition
                    selectedPosition = adapterPosition
                    
                    if (previousSelected != -1) {
                        notifyItemChanged(previousSelected)
                    }
                    notifyItemChanged(selectedPosition)
                    
                    onOptionSelected(adapterPosition, options[adapterPosition])
                }
            }
        }
    }
    
    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): OptionViewHolder {
        val view = LayoutInflater.from(parent.context)
            .inflate(R.layout.item_quiz_option, parent, false)
        return OptionViewHolder(view)
    }
    
    override fun onBindViewHolder(holder: OptionViewHolder, position: Int) {
        val letters = listOf("A", "B", "C", "D")
        holder.letterText.text = letters.getOrElse(position) { "" }
        holder.optionText.text = options[position]
        
        // Update background based on state
        val backgroundRes = when {
            showResult && position == correctPosition -> R.drawable.bg_option_correct
            showResult && position == selectedPosition && position != correctPosition -> R.drawable.bg_option_wrong
            position == selectedPosition -> R.drawable.bg_option_selected
            else -> R.drawable.bg_option_normal
        }
        holder.container.setBackgroundResource(backgroundRes)
    }
    
    override fun getItemCount(): Int = options.size
    
    fun updateOptions(newOptions: List<String>) {
        options = newOptions
        selectedPosition = -1
        correctPosition = -1
        showResult = false
        notifyDataSetChanged()
    }
    
    fun showResult(correctAnswer: String) {
        showResult = true
        correctPosition = options.indexOf(correctAnswer)
        notifyDataSetChanged()
    }
    
    fun getSelectedPosition(): Int = selectedPosition
    
    fun getSelectedAnswer(): String? {
        return if (selectedPosition >= 0 && selectedPosition < options.size) {
            options[selectedPosition]
        } else null
    }
    
    fun resetSelection() {
        selectedPosition = -1
        correctPosition = -1
        showResult = false
        notifyDataSetChanged()
    }
}
```

### MemoryCardAdapter.kt

```kotlin
package com.angonurse.game2.adapters

import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.view.animation.AccelerateDecelerateInterpolator
import android.widget.ImageView
import android.widget.TextView
import androidx.cardview.widget.CardView
import androidx.recyclerview.widget.RecyclerView
import com.angonurse.game2.R
import com.angonurse.game2.models.MemoryCard

class MemoryCardAdapter(
    private var cards: List<MemoryCard>,
    private var cardSize: Int,
    private val onCardClicked: (Int) -> Unit
) : RecyclerView.Adapter<MemoryCardAdapter.CardViewHolder>() {
    
    inner class CardViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) {
        val cardView: CardView = itemView.findViewById(R.id.cardView)
        val cardBack: TextView = itemView.findViewById(R.id.cardBack)
        val cardImage: ImageView = itemView.findViewById(R.id.cardImage)
        
        init {
            itemView.setOnClickListener {
                if (adapterPosition != RecyclerView.NO_POSITION) {
                    onCardClicked(adapterPosition)
                }
            }
        }
    }
    
    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): CardViewHolder {
        val view = LayoutInflater.from(parent.context)
            .inflate(R.layout.item_memory_card, parent, false)
        
        // Set card size
        val params = view.layoutParams
        params.width = cardSize
        params.height = cardSize
        view.layoutParams = params
        
        return CardViewHolder(view)
    }
    
    override fun onBindViewHolder(holder: CardViewHolder, position: Int) {
        val card = cards[position]
        
        if (card.isFlipped || card.isMatched) {
            holder.cardBack.visibility = View.GONE
            holder.cardImage.visibility = View.VISIBLE
            holder.cardImage.setImageResource(card.imageResId)
            holder.cardView.setCardBackgroundColor(
                holder.itemView.context.getColor(R.color.memory_card_front)
            )
        } else {
            holder.cardBack.visibility = View.VISIBLE
            holder.cardImage.visibility = View.GONE
            holder.cardView.setCardBackgroundColor(
                holder.itemView.context.getColor(R.color.memory_card_back)
            )
        }
        
        // Dim matched cards slightly
        holder.cardView.alpha = if (card.isMatched) 0.7f else 1f
    }
    
    override fun getItemCount(): Int = cards.size
    
    fun updateCards(newCards: List<MemoryCard>, newCardSize: Int) {
        cards = newCards
        cardSize = newCardSize
        notifyDataSetChanged()
    }
    
    fun flipCard(position: Int, callback: () -> Unit) {
        notifyItemChanged(position)
        
        // Simple animation delay
        android.os.Handler(android.os.Looper.getMainLooper()).postDelayed({
            callback()
        }, 100)
    }
    
    fun unflipCards(positions: List<Int>) {
        positions.forEach { position ->
            notifyItemChanged(position)
        }
    }
}
```

---

## 🎯 Activities

### MainActivity.kt

```kotlin
package com.angonurse.game2

import android.content.Intent
import android.os.Bundle
import android.os.Handler
import android.os.Looper
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        
        // Splash delay
        Handler(Looper.getMainLooper()).postDelayed({
            startActivity(Intent(this, WelcomeActivity::class.java))
            finish()
        }, 1500)
    }
}
```

### WelcomeActivity.kt

```kotlin
package com.angonurse.game2

import android.content.Intent
import android.os.Bundle
import android.view.animation.AnimationUtils
import androidx.appcompat.app.AppCompatActivity
import com.angonurse.game2.databinding.ActivityWelcomeBinding
import com.angonurse.game2.managers.SoundManager
import com.angonurse.game2.utils.PreferencesHelper

class WelcomeActivity : AppCompatActivity() {
    
    private lateinit var binding: ActivityWelcomeBinding
    private lateinit var soundManager: SoundManager
    private lateinit var prefsHelper: PreferencesHelper
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityWelcomeBinding.inflate(layoutInflater)
        setContentView(binding.root)
        
        prefsHelper = PreferencesHelper(this)
        soundManager = SoundManager(this)
        soundManager.setMusicEnabled(prefsHelper.isMusicEnabled)
        soundManager.setSoundEnabled(prefsHelper.isSoundEnabled)
        
        setupAnimations()
        setupClickListeners()
    }
    
    private fun setupAnimations() {
        // Fade in animation for elements
        val fadeIn = AnimationUtils.loadAnimation(this, android.R.anim.fade_in)
        fadeIn.duration = 800
        
        binding.logoImage.startAnimation(fadeIn)
        binding.titleText.startAnimation(fadeIn)
        binding.subtitleText.startAnimation(fadeIn)
    }
    
    private fun setupClickListeners() {
        binding.btnStartQuiz.setOnClickListener {
            startActivity(Intent(this, QuizActivity::class.java))
        }
        
        binding.btnMemoryGame.setOnClickListener {
            startActivity(Intent(this, MemoryGameActivity::class.java))
        }
        
        binding.btnAbout.setOnClickListener {
            startActivity(Intent(this, AboutActivity::class.java))
        }
        
        binding.btnSettings.setOnClickListener {
            startActivity(Intent(this, SettingsActivity::class.java))
        }
    }
    
    override fun onResume() {
        super.onResume()
        // Reload preferences
        soundManager.setMusicEnabled(prefsHelper.isMusicEnabled)
        soundManager.setSoundEnabled(prefsHelper.isSoundEnabled)
    }
    
    override fun onDestroy() {
        super.onDestroy()
        soundManager.release()
    }
}
```

### QuizActivity.kt

```kotlin
package com.angonurse.game2

import android.content.Intent
import android.os.Bundle
import android.os.CountDownTimer
import android.os.Handler
import android.os.Looper
import android.os.VibrationEffect
import android.os.Vibrator
import android.view.View
import androidx.appcompat.app.AlertDialog
import androidx.appcompat.app.AppCompatActivity
import androidx.recyclerview.widget.LinearLayoutManager
import com.angonurse.game2.adapters.QuizOptionAdapter
import com.angonurse.game2.databinding.ActivityQuizBinding
import com.angonurse.game2.managers.QuizManager
import com.angonurse.game2.managers.SoundManager
import com.angonurse.game2.utils.PreferencesHelper

class QuizActivity : AppCompatActivity() {
    
    private lateinit var binding: ActivityQuizBinding
    private lateinit var quizManager: QuizManager
    private lateinit var soundManager: SoundManager
    private lateinit var prefsHelper: PreferencesHelper
    private var optionAdapter: QuizOptionAdapter? = null
    
    private var countDownTimer: CountDownTimer? = null
    private var timeLeftInMillis: Long = 0
    private var selectedAnswer: String? = null
    private var isQuizInitialized = false
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        try {
            binding = ActivityQuizBinding.inflate(layoutInflater)
            setContentView(binding.root)
            
            prefsHelper = PreferencesHelper(this)
            soundManager = SoundManager(this)
            soundManager.setMusicEnabled(prefsHelper.isMusicEnabled)
            soundManager.setSoundEnabled(prefsHelper.isSoundEnabled)
            
            quizManager = QuizManager()
            quizManager.initQuiz()
            
            setupRecyclerView()
            setupClickListeners()
            
            // Delay first question display to ensure adapter is ready
            Handler(Looper.getMainLooper()).postDelayed({
                displayQuestion()
                isQuizInitialized = true
                soundManager.startBackgroundMusic()
            }, 100)
            
        } catch (e: Exception) {
            e.printStackTrace()
            finish()
        }
    }
    
    private fun setupRecyclerView() {
        val currentQuestion = quizManager.getCurrentQuestion()
        val initialOptions = currentQuestion?.options ?: emptyList()
        
        optionAdapter = QuizOptionAdapter(initialOptions) { position, answer ->
            selectedAnswer = answer
            binding.btnConfirm.isEnabled = true
            binding.btnConfirm.alpha = 1f
        }
        
        binding.optionsRecyclerView.apply {
            layoutManager = LinearLayoutManager(this@QuizActivity)
            adapter = optionAdapter
            isNestedScrollingEnabled = false
            itemAnimator = null // Disable animations to prevent crashes
        }
    }
    
    private fun setupClickListeners() {
        binding.btnConfirm.setOnClickListener {
            if (selectedAnswer != null) {
                confirmAnswer()
            }
        }
    }
    
    private fun displayQuestion() {
        try {
            val question = quizManager.getCurrentQuestion()
            if (question == null) {
                finishQuiz()
                return
            }
            
            // Update UI
            binding.questionProgress.text = getString(
                R.string.question_label, 
                quizManager.getCurrentIndex() + 1, 
                quizManager.getTotalQuestions()
            )
            
            val totalQuestions = quizManager.getTotalQuestions()
            val progress = if (totalQuestions > 0) {
                ((quizManager.getCurrentIndex()) * 100) / totalQuestions
            } else 0
            binding.overallProgress.progress = progress
            
            binding.questionText.text = question.text
            optionAdapter?.updateOptions(question.options)
            
            // Reset button state
            selectedAnswer = null
            binding.btnConfirm.isEnabled = false
            binding.btnConfirm.alpha = 0.5f
            binding.btnConfirm.text = if (quizManager.isLastQuestion()) {
                getString(R.string.btn_finish)
            } else {
                getString(R.string.btn_confirm)
            }
            
            // Start timer
            startTimer()
        } catch (e: Exception) {
            e.printStackTrace()
            finishQuiz()
        }
    }
    
    private fun startTimer() {
        countDownTimer?.cancel()
        
        val totalTime = quizManager.getTimePerQuestion() * 1000L
        timeLeftInMillis = totalTime
        
        countDownTimer = object : CountDownTimer(totalTime, 1000) {
            override fun onTick(millisUntilFinished: Long) {
                timeLeftInMillis = millisUntilFinished
                updateTimerUI()
            }
            
            override fun onFinish() {
                timeUp()
            }
        }.start()
    }
    
    private fun updateTimerUI() {
        try {
            val seconds = (timeLeftInMillis / 1000).toInt()
            val minutes = seconds / 60
            val secs = seconds % 60
            
            binding.timerText.text = String.format("%02d:%02d", minutes, secs)
            
            val totalTime = quizManager.getTimePerQuestion() * 1000
            val percentage = if (totalTime > 0) {
                ((timeLeftInMillis * 100) / totalTime).toInt()
            } else 100
            binding.timerProgress.progress = percentage
            
            // Warning state when less than 20%
            if (percentage < 20) {
                binding.timerText.setTextColor(getColor(R.color.warning))
                binding.timerIcon.setColorFilter(getColor(R.color.warning))
            } else {
                binding.timerText.setTextColor(getColor(R.color.text_primary))
                binding.timerIcon.setColorFilter(getColor(R.color.primary))
            }
        } catch (e: Exception) {
            e.printStackTrace()
        }
    }
    
    private fun timeUp() {
        try {
            AlertDialog.Builder(this)
                .setTitle(getString(R.string.time_up))
                .setMessage(getString(R.string.time_up_message))
                .setPositiveButton(getString(R.string.ok)) { _, _ ->
                    // Register empty answer and continue
                    quizManager.answerQuestion("")
                    proceedToNextQuestion()
                }
                .setCancelable(false)
                .show()
        } catch (e: Exception) {
            e.printStackTrace()
            quizManager.answerQuestion("")
            proceedToNextQuestion()
        }
    }
    
    private fun confirmAnswer() {
        try {
            val answer = selectedAnswer ?: return
            val question = quizManager.getCurrentQuestion() ?: return
            
            countDownTimer?.cancel()
            
            val isCorrect = quizManager.answerQuestion(answer)
            
            // Play sound
            if (isCorrect) {
                soundManager.playMatch()
            } else {
                soundManager.playMismatch()
            }
            
            // Vibrate
            if (prefsHelper.isVibrationEnabled) {
                try {
                    val vibrator = getSystemService(Vibrator::class.java)
                    val duration = if (isCorrect) 100L else 200L
                    vibrator?.vibrate(VibrationEffect.createOneShot(duration, VibrationEffect.DEFAULT_AMPLITUDE))
                } catch (e: Exception) {
                    // Ignore vibration errors
                }
            }
            
            // Show result
            optionAdapter?.showResult(question.correctAnswer)
            binding.btnConfirm.isEnabled = false
            
            // Proceed after delay
            Handler(Looper.getMainLooper()).postDelayed({
                proceedToNextQuestion()
            }, 1500)
        } catch (e: Exception) {
            e.printStackTrace()
            proceedToNextQuestion()
        }
    }
    
    private fun proceedToNextQuestion() {
        if (quizManager.nextQuestion()) {
            displayQuestion()
        } else {
            finishQuiz()
        }
    }
    
    private fun finishQuiz() {
        try {
            soundManager.stopBackgroundMusic()
            
            val intent = Intent(this, ResultActivity::class.java).apply {
                putExtra("score", quizManager.getScore())
                putExtra("total", quizManager.getTotalQuestions())
                putExtra("percentage", quizManager.getPercentage())
                putExtra("correct", quizManager.getCorrectCount())
                putExtra("wrong", quizManager.getWrongCount())
            }
            startActivity(intent)
            finish()
        } catch (e: Exception) {
            e.printStackTrace()
            finish()
        }
    }
    
    override fun onDestroy() {
        super.onDestroy()
        countDownTimer?.cancel()
        countDownTimer = null
        try {
            soundManager.release()
        } catch (e: Exception) {
            e.printStackTrace()
        }
    }
    
    @Deprecated("Deprecated in Java")
    override fun onBackPressed() {
        try {
            AlertDialog.Builder(this)
                .setTitle("Sair do Quiz?")
                .setMessage("O seu progresso será perdido.")
                .setPositiveButton("Sair") { _, _ ->
                    countDownTimer?.cancel()
                    soundManager.stopBackgroundMusic()
                    super.onBackPressed()
                }
                .setNegativeButton("Continuar", null)
                .show()
        } catch (e: Exception) {
            super.onBackPressed()
        }
    }
}
```

### MemoryGameActivity.kt

```kotlin
package com.angonurse.game2

import android.content.Intent
import android.os.Bundle
import android.os.Handler
import android.os.Looper
import android.os.SystemClock
import android.view.LayoutInflater
import android.widget.Button
import androidx.appcompat.app.AlertDialog
import androidx.appcompat.app.AppCompatActivity
import androidx.recyclerview.widget.GridLayoutManager
import com.angonurse.game2.adapters.MemoryCardAdapter
import com.angonurse.game2.databinding.ActivityMemoryGameBinding
import com.angonurse.game2.managers.MemoryGameManager
import com.angonurse.game2.managers.SoundManager
import com.angonurse.game2.models.DifficultyLevel
import com.angonurse.game2.utils.PreferencesHelper
import com.angonurse.game2.utils.ScreenUtils

class MemoryGameActivity : AppCompatActivity() {
    
    private lateinit var binding: ActivityMemoryGameBinding
    private lateinit var gameManager: MemoryGameManager
    private lateinit var soundManager: SoundManager
    private lateinit var prefsHelper: PreferencesHelper
    private lateinit var cardAdapter: MemoryCardAdapter
    
    private var startTime: Long = 0
    private var timerHandler: Handler? = null
    private var timerRunnable: Runnable? = null
    private var difficulty: DifficultyLevel = DifficultyLevel.EASY
    
    // Lista de imagens placeholder - substitua pelos seus recursos reais
    private val easyImages = listOf(
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground
    )
    
    private val mediumImages = listOf(
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground
    )
    
    private val hardImages = listOf(
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground
    )
    
    private val powerImages = listOf(
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground,
        R.drawable.ic_launcher_foreground
    )
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMemoryGameBinding.inflate(layoutInflater)
        setContentView(binding.root)
        
        prefsHelper = PreferencesHelper(this)
        soundManager = SoundManager(this)
        soundManager.setMusicEnabled(prefsHelper.isMusicEnabled)
        soundManager.setSoundEnabled(prefsHelper.isSoundEnabled)
        
        showDifficultyDialog()
    }
    
    private fun showDifficultyDialog() {
        val dialogView = LayoutInflater.from(this)
            .inflate(R.layout.dialog_difficulty, null)
        
        val dialog = AlertDialog.Builder(this)
            .setView(dialogView)
            .setCancelable(false)
            .create()
        
        dialogView.findViewById<Button>(R.id.btnEasy).setOnClickListener {
            difficulty = DifficultyLevel.EASY
            dialog.dismiss()
            startGame()
        }
        
        dialogView.findViewById<Button>(R.id.btnMedium).setOnClickListener {
            difficulty = DifficultyLevel.MEDIUM
            dialog.dismiss()
            startGame()
        }
        
        dialogView.findViewById<Button>(R.id.btnHard).setOnClickListener {
            difficulty = DifficultyLevel.HARD
            dialog.dismiss()
            startGame()
        }
        
        dialogView.findViewById<Button>(R.id.btnPower).setOnClickListener {
            difficulty = DifficultyLevel.POWER
            dialog.dismiss()
            startGame()
        }
        
        dialog.show()
    }
    
    private fun startGame() {
        val images = when (difficulty) {
            DifficultyLevel.EASY -> easyImages
            DifficultyLevel.MEDIUM -> mediumImages
            DifficultyLevel.HARD -> hardImages
            DifficultyLevel.POWER -> powerImages
        }
        
        gameManager = MemoryGameManager(difficulty)
        gameManager.initGame(images)
        
        setupRecyclerView()
        startTimer()
        updateUI()
        
        soundManager.startBackgroundMusic()
    }
    
    private fun setupRecyclerView() {
        val columns = gameManager.getColumns()
        val totalCards = gameManager.getCards().size
        
        // Calculate available height for cards
        binding.cardsRecyclerView.post {
            val availableHeight = binding.cardsRecyclerView.height
            val cardSize = ScreenUtils.calculateCardSize(this, columns, totalCards, availableHeight)
            
            cardAdapter = MemoryCardAdapter(gameManager.getCards(), cardSize) { position ->
                onCardClicked(position)
            }
            
            binding.cardsRecyclerView.apply {
                layoutManager = GridLayoutManager(this@MemoryGameActivity, columns)
                adapter = cardAdapter
                setHasFixedSize(true)
            }
        }
    }
    
    private fun onCardClicked(position: Int) {
        if (gameManager.isProcessing()) return
        
        when (gameManager.flipCard(position)) {
            MemoryGameManager.FlipResult.FIRST_CARD -> {
                cardAdapter.notifyItemChanged(position)
            }
            MemoryGameManager.FlipResult.SECOND_CARD -> {
                cardAdapter.notifyItemChanged(position)
                gameManager.setProcessing(true)
                
                Handler(Looper.getMainLooper()).postDelayed({
                    checkMatch()
                }, 800)
            }
            else -> { /* Ignore */ }
        }
        
        updateUI()
    }
    
    private fun checkMatch() {
        when (gameManager.checkMatch()) {
            MemoryGameManager.MatchResult.MATCH -> {
                soundManager.playMatch()
                gameManager.setProcessing(false)
                updateUI()
            }
            MemoryGameManager.MatchResult.NO_MATCH -> {
                soundManager.playMismatch()
                gameManager.resetUnmatched()
                cardAdapter.notifyDataSetChanged()
                gameManager.setProcessing(false)
            }
            MemoryGameManager.MatchResult.GAME_COMPLETE -> {
                soundManager.playMatch()
                Handler(Looper.getMainLooper()).postDelayed({
                    finishGame()
                }, 500)
            }
        }
        updateUI()
    }
    
    private fun updateUI() {
        binding.pairsText.text = "${gameManager.getPairsFound()}/${gameManager.getPairsCount()}"
        binding.movesText.text = "${gameManager.getMoves()}"
    }
    
    private fun startTimer() {
        startTime = SystemClock.elapsedRealtime()
        timerHandler = Handler(Looper.getMainLooper())
        timerRunnable = object : Runnable {
            override fun run() {
                val elapsed = SystemClock.elapsedRealtime() - startTime
                val seconds = (elapsed / 1000).toInt()
                val minutes = seconds / 60
                val secs = seconds % 60
                binding.timerText.text = String.format("%02d:%02d", minutes, secs)
                timerHandler?.postDelayed(this, 1000)
            }
        }
        timerHandler?.post(timerRunnable!!)
    }
    
    private fun stopTimer(): String {
        timerHandler?.removeCallbacks(timerRunnable!!)
        val elapsed = SystemClock.elapsedRealtime() - startTime
        val seconds = (elapsed / 1000).toInt()
        val minutes = seconds / 60
        val secs = seconds % 60
        return String.format("%02d:%02d", minutes, secs)
    }
    
    private fun finishGame() {
        val time = stopTimer()
        soundManager.stopBackgroundMusic()
        
        val intent = Intent(this, MemoryResultActivity::class.java).apply {
            putExtra("time", time)
            putExtra("moves", gameManager.getMoves())
            putExtra("difficulty", difficulty.name)
        }
        startActivity(intent)
        finish()
    }
    
    override fun onDestroy() {
        super.onDestroy()
        timerHandler?.removeCallbacksAndMessages(null)
        soundManager.release()
    }
    
    override fun onBackPressed() {
        AlertDialog.Builder(this)
            .setTitle("Sair do Jogo?")
            .setMessage("O seu progresso será perdido.")
            .setPositiveButton("Sair") { _, _ ->
                soundManager.stopBackgroundMusic()
                super.onBackPressed()
            }
            .setNegativeButton("Continuar", null)
            .show()
    }
}
```

### ResultActivity.kt

```kotlin
package com.angonurse.game2

import android.content.Intent
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import com.angonurse.game2.databinding.ActivityResultBinding

class ResultActivity : AppCompatActivity() {
    
    private lateinit var binding: ActivityResultBinding
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityResultBinding.inflate(layoutInflater)
        setContentView(binding.root)
        
        val score = intent.getIntExtra("score", 0)
        val total = intent.getIntExtra("total", 0)
        val percentage = intent.getIntExtra("percentage", 0)
        val correct = intent.getIntExtra("correct", 0)
        val wrong = intent.getIntExtra("wrong", 0)
        
        displayResults(percentage, correct, wrong)
        setupClickListeners()
    }
    
    private fun displayResults(percentage: Int, correct: Int, wrong: Int) {
        binding.percentageText.text = getString(R.string.percentage, percentage)
        binding.correctCount.text = correct.toString()
        binding.wrongCount.text = wrong.toString()
        
        // Set performance message and emoji
        val (message, emoji) = when {
            percentage >= 90 -> Pair(getString(R.string.performance_excellent), "🏆")
            percentage >= 70 -> Pair(getString(R.string.performance_good), "🎉")
            percentage >= 50 -> Pair(getString(R.string.performance_average), "💪")
            else -> Pair(getString(R.string.performance_poor), "📚")
        }
        
        binding.performanceMessage.text = message
        binding.trophyIcon.text = emoji
        
        // Set percentage color
        val color = when {
            percentage >= 70 -> getColor(R.color.success)
            percentage >= 50 -> getColor(R.color.warning)
            else -> getColor(R.color.error)
        }
        binding.percentageText.setTextColor(color)
    }
    
    private fun setupClickListeners() {
        binding.btnTryAgain.setOnClickListener {
            startActivity(Intent(this, QuizActivity::class.java))
            finish()
        }
        
        binding.btnHome.setOnClickListener {
            startActivity(Intent(this, WelcomeActivity::class.java))
            finishAffinity()
        }
        
        binding.btnReview.setOnClickListener {
            // TODO: Implement review activity
        }
    }
}
```

### MemoryResultActivity.kt

```kotlin
package com.angonurse.game2

import android.content.Intent
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import com.angonurse.game2.databinding.ActivityMemoryResultBinding

class MemoryResultActivity : AppCompatActivity() {
    
    private lateinit var binding: ActivityMemoryResultBinding
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMemoryResultBinding.inflate(layoutInflater)
        setContentView(binding.root)
        
        val time = intent.getStringExtra("time") ?: "00:00"
        val moves = intent.getIntExtra("moves", 0)
        
        binding.timeText.text = time
        binding.movesText.text = moves.toString()
        
        setupClickListeners()
    }
    
    private fun setupClickListeners() {
        binding.btnPlayAgain.setOnClickListener {
            startActivity(Intent(this, MemoryGameActivity::class.java))
            finish()
        }
        
        binding.btnHome.setOnClickListener {
            startActivity(Intent(this, WelcomeActivity::class.java))
            finishAffinity()
        }
    }
}
```

### AboutActivity.kt

```kotlin
package com.angonurse.game2

import android.content.Intent
import android.net.Uri
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import com.angonurse.game2.databinding.ActivityAboutBinding

class AboutActivity : AppCompatActivity() {
    
    private lateinit var binding: ActivityAboutBinding
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityAboutBinding.inflate(layoutInflater)
        setContentView(binding.root)
        
        setupClickListeners()
    }
    
    private fun setupClickListeners() {
        binding.btnBack.setOnClickListener {
            finish()
        }
        
        binding.btnFacebook.setOnClickListener {
            val intent = Intent(Intent.ACTION_VIEW).apply {
                data = Uri.parse("https://www.facebook.com/angonurse")
            }
            startActivity(intent)
        }
    }
}
```

### SettingsActivity.kt

```kotlin
package com.angonurse.game2

import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import com.angonurse.game2.databinding.ActivitySettingsBinding
import com.angonurse.game2.utils.PreferencesHelper

class SettingsActivity : AppCompatActivity() {
    
    private lateinit var binding: ActivitySettingsBinding
    private lateinit var prefsHelper: PreferencesHelper
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivitySettingsBinding.inflate(layoutInflater)
        setContentView(binding.root)
        
        prefsHelper = PreferencesHelper(this)
        
        loadSettings()
        setupClickListeners()
    }
    
    private fun loadSettings() {
        binding.switchMusic.isChecked = prefsHelper.isMusicEnabled
        binding.switchSound.isChecked = prefsHelper.isSoundEnabled
        binding.switchVibration.isChecked = prefsHelper.isVibrationEnabled
    }
    
    private fun setupClickListeners() {
        binding.btnBack.setOnClickListener {
            finish()
        }
        
        binding.switchMusic.setOnCheckedChangeListener { _, isChecked ->
            prefsHelper.isMusicEnabled = isChecked
        }
        
        binding.switchSound.setOnCheckedChangeListener { _, isChecked ->
            prefsHelper.isSoundEnabled = isChecked
        }
        
        binding.switchVibration.setOnCheckedChangeListener { _, isChecked ->
            prefsHelper.isVibrationEnabled = isChecked
        }
    }
}
```

---

## 🎵 Arquivos de Áudio

Coloque os seguintes arquivos na pasta `res/raw/`:

1. **sound_match.mp3** - Som para quando acerta
2. **sound_mismatch.mp3** - Som para quando erra
3. **musica.aac** - Música de fundo

---

## 📱 Compilação no RV2IDE

### Passos para Compilar:

1. **Criar Novo Projeto**
   - Abra o RV2IDE
   - Selecione "New Project"
   - Nome: `AngoNurseGame`
   - Package: `com.angonurse.game2`
   - Linguagem: Kotlin

2. **Estrutura de Pastas**
   - Crie a estrutura de pastas conforme indicado acima

3. **Copiar Arquivos**
   - Copie todos os arquivos `.kt` para as pastas correspondentes
   - Copie todos os arquivos `.xml` para as pastas de layout/drawable/values

4. **Recursos**
   - Adicione as imagens do jogo da memória em `res/drawable/`
   - Adicione os áudios em `res/raw/`
   - Adicione o ícone do app em `res/mipmap/`

5. **Compilar**
   - Clique em "Build" → "Build APK"
   - Aguarde a compilação
   - O APK estará em `app/build/outputs/apk/`

### Troubleshooting RV2IDE:

**Erro de Gradle:**
- Verifique a versão do Gradle no `build.gradle`
- Se usar AIDE, altere para Groovy syntax: `build.gradle` em vez de `build.gradle.kts`

**Erro de SDK:**
- Certifique-se que tem o SDK 36 instalado
- Se não tiver SDK 36, pode usar `compileSdk = 34`

**Erro de Kotlin:**
- Atualize o plugin Kotlin para 1.9.22
- Se aparecer erro de versão, use `1.8.20`

**App crasha ao abrir Quiz:**
- Verifique se todos os arquivos XML de layout estão corretos
- Verifique se `item_quiz_option.xml` foi criado em `res/layout/`
- Verifique se as cores estão definidas em `colors.xml`

**Botões cortados na tela Welcome:**
- Use o novo layout `activity_welcome.xml` com ConstraintLayout aninhado
- Garanta que `fitsSystemWindows="true"` está definido
- Teste em diferentes tamanhos de ecrã

**Crash ao responder pergunta:**
- Verifique se `QuizManager.kt` tem as 45 perguntas corretamente definidas
- Verifique se `SoundManager.kt` encontra os arquivos de áudio em `res/raw/`
- Se não tiver áudios, comente as linhas de som temporariamente

**Imagens não aparecem no jogo da memória:**
- Adicione imagens reais em `res/drawable/`
- Substitua `R.drawable.ic_launcher_foreground` pelos nomes corretos

**Layout não adaptativo:**
- Verifique se `ScreenUtils.kt` está calculando corretamente os tamanhos
- Use `wrap_content` e `0dp` com weights em vez de dimensões fixas

### Conversão para AIDE (Groovy):

Se usar AIDE em vez de RV2IDE, converta os arquivos Gradle para Groovy:

**build.gradle (app):**
```groovy
plugins {
    id 'com.android.application'
    id 'org.jetbrains.kotlin.android'
}

android {
    namespace 'com.angonurse.game2'
    compileSdk 34

    defaultConfig {
        applicationId "com.angonurse.game2"
        minSdk 21
        targetSdk 34
        versionCode 1
        versionName "1.0.0"
    }

    buildTypes {
        release {
            minifyEnabled true
            shrinkResources true
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }

    compileOptions {
        sourceCompatibility JavaVersion.VERSION_17
        targetCompatibility JavaVersion.VERSION_17
    }

    kotlinOptions {
        jvmTarget = '17'
    }

    buildFeatures {
        viewBinding true
    }
}

dependencies {
    implementation 'androidx.core:core-ktx:1.12.0'
    implementation 'androidx.appcompat:appcompat:1.6.1'
    implementation 'com.google.android.material:material:1.11.0'
    implementation 'androidx.constraintlayout:constraintlayout:2.1.4'
    implementation 'androidx.recyclerview:recyclerview:1.3.2'
    implementation 'androidx.cardview:cardview:1.0.0'
    implementation 'androidx.lifecycle:lifecycle-runtime-ktx:2.7.0'
}
```

---

## 🎨 Personalização de Imagens

Para o jogo da memória, substitua `R.drawable.ic_launcher_foreground` pelos seus recursos de imagem reais:

```kotlin
// Em MemoryGameActivity.kt
private val easyImages = listOf(
    R.drawable.easy_puzzle_1,
    R.drawable.easy_puzzle_2,
    R.drawable.easy_rubiks_1,
    R.drawable.easy_rubiks_2
)
// ... etc
```

---

## 📄 Licença

MIT License - AngoNurse © 2024

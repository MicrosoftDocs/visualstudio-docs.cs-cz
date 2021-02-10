---
title: Kompilování a sestavení kódu TypeScript pomocí npm
description: Naučte se, jak přidat do projektů aplikace Visual Studio podporu TypeScript pomocí node Package Manageru (npm).
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 966b08a912a7bab59998daf39590a6fd46920eb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969526"
---
# <a name="compile-typescript-code-nodejs"></a>Kompilovat kód TypeScriptu (Node.js)

Podporu TypeScript můžete do projektů přidat pomocí TypeScript SDK, která je dostupná ve výchozím nastavení v instalačním programu sady Visual Studio nebo pomocí npm. Pro projekty vyvinuté v aplikaci Visual Studio 2019 doporučujeme použít balíček TypeScript npm pro větší přenositelnost napříč různými platformami a prostředími.

U ASP.NET Core projektů doporučujeme místo toho použít [balíček NuGet](../javascript/compile-typescript-code-nuget.md) .

## <a name="add-typescript-support-using-npm"></a>Přidání podpory TypeScript pomocí npm

[Balíček TypeScript npm](https://www.npmjs.com/package/typescript) přidává podporu TypeScript. Při instalaci balíčku npm pro TypeScript 2,1 nebo vyšší do projektu se v editoru načte odpovídající verze jazykové služby TypeScript.

1. [Podle pokynů](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json) nainstalujte Node.js vývojové úlohy a modul runtime Node.js.

   Pro nejjednodušší integraci se sadou Visual Studio vytvořte projekt pomocí jedné z Node.js šablon TypeScript, jako je prázdná Node.js šablona webové aplikace. V opačném případě použijte šablonu Node.js JavaScriptu, která je součástí sady Visual Studio, a postupujte podle pokynů nebo použijte [otevřený projekt složky](../javascript/develop-javascript-code-without-solutions-projects.md) .

1. Pokud projekt ještě není zahrnutý, nainstalujte [balíček TypeScript npm](https://www.npmjs.com/package/typescript).

   Z Průzkumník řešení (pravé podokno) otevřete *package.js* v kořenovém adresáři projektu. Uvedené balíčky odpovídají balíčkům v uzlu npm v Průzkumník řešení. Další informace najdete v tématu [Správa balíčků npm](../javascript/npm-package-management.md).

   V případě Node.js projektu můžete balíček TypeScript npm nainstalovat pomocí příkazového řádku nebo rozhraní IDE. Pokud chcete nainstalovat pomocí prostředí IDE, klikněte pravým tlačítkem na uzel npm v Průzkumník řešení, vyberte **instalovat nový balíček npm**, vyhledejte **TypeScript** a nainstalujte balíček.

   V okně **výstup** zkontrolujte možnost **npm** a zobrazí se průběh instalace balíčku. Nainstalovaný balíček se zobrazí pod uzlem **npm** v Průzkumník řešení.

1. Pokud projekt ještě neobsahuje, přidejte soubor *. tsconfig* do kořenového adresáře projektu. Chcete-li přidat soubor, klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **přidat > novou položku**. Zvolte **konfigurační soubor JSON pro TypeScript** a pak klikněte na **Přidat**.

   Visual Studio přidá *tsconfig.js* do souboru do kořenového adresáře projektu. Tento soubor můžete použít ke [konfiguraci možností](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) pro kompilátor TypeScript.

1. Otevřete *tsconfig.jsna* a aktualizujte, abyste nastavili požadované možnosti kompilátoru.

   Následuje příklad jednoduchého *tsconfig.js* souboru.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "dist"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   V tomto příkladu:
   - *Zahrnout* instruuje kompilátor, kde se mají najít soubory TypeScript (*. TS).
   - možnost *outDir* určuje výstupní složku pro soubory prostého JavaScriptu, které jsou přepsány kompilátorem TypeScript.
   - možnost *sourceMap* označuje, zda kompilátor generuje soubory *sourceMap* .

   Předchozí konfigurace poskytuje jenom základní úvodní informace ke konfiguraci TypeScript. Informace o dalších možnostech najdete v tématu [tsconfig.js](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="build-the-application"></a>Sestavení aplikace

1. Přidejte do projektu soubory TypeScript (*. TS*) nebo TypeScript JSX (*. TSX*) a pak přidejte kód TypeScript. Pro jednoduchý příklad TypeScript použijte následující:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. V *package.jsna*, přidejte podporu pro příkazy sady Visual Studio pro sestavení a vyčištění pomocí následujících skriptů.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   Pokud potřebujete sestavit pomocí nástroje třetí strany, jako je například Webpack, můžete do *package.js* do souboru přidat skript sestavení příkazového řádku:

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   Příklad použití nástroje Webpack s reagující a konfiguračním souborem webového balíčku najdete v tématu [Vytvoření webové aplikace s Node.js a reakce](../javascript/tutorial-nodejs-with-react-and-jsx.md).

   Příklad použití Vue.js s TypeScript najdete v tématu [vytvoření Vue.js aplikace](/javascript/create-application-with-vuejs).

1. Pokud potřebujete nakonfigurovat možnosti, jako je úvodní stránka, cesta k Node.js runtime, port aplikace nebo běhové argumenty, klikněte pravým tlačítkem myši na uzel projektu v Průzkumník řešení a vyberte **vlastnosti**.

   >[!NOTE]
   > Při konfiguraci nástrojů třetích stran Node.js projekty nepoužívají cesty, které jsou nakonfigurované v nabídce **nástroje**  >  **Možnosti**  >  **projekty a řešení**  >  **webové Správa balíčků**  >  **externí webové nástroje**. Tato nastavení se používají pro ostatní typy projektů.

1. Vyberte **sestavení řešení sestavení >**.

   I když se aplikace při spuštění automaticky vytvoří, chceme se podívat na něco, co se děje během procesu sestavení:

   Pokud jste vygenerovali zdrojová mapování, otevřete složku zadanou v možnosti *outDir* a najděte vygenerované \* soubory. js spolu se generovanými \* soubory JS. map.

   Zdrojové soubory mapování jsou vyžadovány pro [ladění](../javascript/debug-nodejs.md).

### <a name="run-the-application"></a>Spuštění aplikace

Pokyny ke spuštění aplikace po jejím zkompilování najdete v tématu [Vytvoření první aplikace Node.js](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json#run-the-application).

## <a name="automate-build-tasks"></a>Automatizace úloh sestavení

Pomocí Průzkumníka Spouštěče úloh v sadě Visual Studio můžete automatizovat úlohy pro nástroje třetích stran, jako je npm a Webpack.

- [Npm Task Runner](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) – přidá podporu pro skripty npm definované v *package.jszapnuté*. Podporuje příze.
- [Spouštěč úloh sady Webpack](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) – přidá podporu pro sadu Webpack.
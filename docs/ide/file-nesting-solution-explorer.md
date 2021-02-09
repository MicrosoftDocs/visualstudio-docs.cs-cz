---
title: Pravidla vnořování souborů pro Průzkumník řešení
description: Přečtěte si o Průzkumník řešení pravidel, přednastavení a přizpůsobení pro vnořování souborů.
ms.custom: SEO-VS-2020
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jmartens
ms.openlocfilehash: aa3ca640fed4e32c19defd925a49369890219035
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869450"
---
# <a name="file-nesting-in-solution-explorer"></a>Vnořování souborů v Průzkumníku řešení

**Průzkumník řešení** vnořovat soubory, které jim pomůžou s jejich uspořádáním a usnadnit jejich vyhledání. Například pokud přidáte model Windows Forms formuláře do projektu, soubor kódu formuláře je vnořen pod formulář v **Průzkumník řešení**. V ASP.NET Core projektech je možné vnoření souborů provést podrobněji. Můžete si vybrat mezi přednastavením vnořování souborů **mimo** jiné, **výchozí** a **Web**. Můžete také [přizpůsobit způsob vnoření souborů](#customize-file-nesting) nebo [vytváření nastavení specifických pro konkrétní řešení a projekt](#create-project-specific-settings).

> [!NOTE]
> Tato funkce je momentálně podporovaná jenom pro projekty ASP.NET Core.

## <a name="file-nesting-options"></a>Možnosti vnořování souborů

![Tlačítko pro zapnutí/vypnutí vnořování souborů](media/filenesting_onoff.png)

Dostupné možnosti pro vnořování nepřizpůsobených souborů:

* **Off (vypnuto**): Tato možnost poskytuje nestrukturovaný seznam souborů bez vnoření.

* **Výchozí**: Tato možnost poskytuje výchozí chování vnořování souborů v **Průzkumník řešení**. Pokud pro daný typ projektu neexistuje žádné nastavení, nejsou vnořené žádné soubory v projektu. Pokud nastavení existuje například pro webový projekt, je vnořování použito.

* **Web**: Tato možnost aplikuje chování vnoření **webových** souborů na všechny projekty v aktuálním řešení. Má spoustu pravidel a doporučujeme vám, abyste si ho vyrezervovali a nás řekli, co si myslíte. Následující snímek obrazovky zvýrazňuje několik příkladů chování vnořování souborů, které získáte pomocí této možnosti:

   ![Vnořování souborů v Průzkumníku řešení](media/filenesting.png)

## <a name="customize-file-nesting"></a>Přizpůsobení vnořování souborů

Pokud si nejste spokojeni s tím, co obdržíte předem, můžete vytvořit vlastní vlastní nastavení vnoření souborů, které dá pokyn **Průzkumník řešení** , jak vnořit soubory. Můžete přidat tolik vlastních nastavení vnoření souborů, kolik chcete, a můžete mezi nimi přepínat podle potřeby. Pokud chcete vytvořit nové vlastní nastavení, můžete začít s prázdným souborem nebo můžete použít nastavení **webu** jako výchozí bod:

![Přidat vlastní pravidla vnořování souborů](media/filenesting_addcustom.png)

Jako výchozí bod doporučujeme používat nastavení **webu** , protože je snazší pracovat s něčím, co už funguje. Pokud jako výchozí bod použijete nastavení **webu** , *.filenesting.jsv* souboru vypadá podobně jako v následujícím souboru:

![Jako základ pro vlastní nastavení použijte existující pravidla vnořování souborů.](media/filenesting_editcustom.png)

Pojďme se zaměřit na uzel **dependentFileProviders** a jeho podřízené uzly. Každý podřízený uzel je typ pravidla, které může Visual Studio použít k vnořování souborů. Například **mají stejný název souboru, ale jiné rozšíření** je jeden typ pravidla. Dostupná jsou tato pravidla:

* **extensionToExtension**: Tento typ pravidla můžete použít k vnořování *file.js* v *souboru. TS.*

* **fileSuffixToExtension**: Tento typ pravidla použijte k vnořování *file-vsdoc.js* v části *file.js*

* **addedExtension**: Tento typ pravidla použijte k vnořování *file.html. CSS* pod *file.html*

* **pathSegment**: Tento typ pravidla použijte k vnořování *jquery.min.js* v části *jquery.js*

* **allExtensions**: Tento typ pravidla použijte k vnořování *souboru.* * v části *file.js*

* **fileToFile**: Tento typ pravidla použijte k vnořování *bower.js* pod *. bowerrc*

### <a name="the-extensiontoextension-provider"></a>Poskytovatel extensionToExtension

Tento zprostředkovatel vám umožní definovat pravidla vnořování souborů pomocí určitých přípon souborů. Uvažujte následující příklad:

![Příklady pravidel extentionToExtension](media/filenesting_extensiontoextension.png) ![Příklad efektu extentionToExtension](media/filenesting_extensiontoextension_effect.png)

* *cart.js* je vnořený do *košíku. TS* z důvodu prvního pravidla **extensionToExtension**

* *cart.js* není vnořený do *košík. TSX* , protože **. TS** v pravidlech předchází **. TSX** a může mít jenom jednu nadřazenou položku.

* *funkce Light. CSS* je vnořená do kategorie *Light. Sass* z důvodu druhého pravidla **extensionToExtension**

* *home.html* je vnořený pod *Home.MD* , protože třetí pravidlo **extensionToExtension**

### <a name="the-filesuffixtoextension-provider"></a>Poskytovatel fileSuffixToExtension

Tento zprostředkovatel funguje stejně jako poskytovatel **extensionToExtension** , přičemž jediným rozdílem je, že pravidlo hledá příponu souboru místo pouze rozšíření. Uvažujte následující příklad:

![Příklady pravidel fileSuffixToExtension](media/filenesting_filesuffixtoextension.png) ![Příklad efektu fileSuffixToExtension](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js* je v rámci *portal.js* vnořený kvůli **fileSuffixToExtension** pravidlu.

* každý další aspekt pravidla funguje stejným způsobem jako **extensionToExtension**

### <a name="the-addedextension-provider"></a>Poskytovatel addedExtension

Tento zprostředkovatel vnořovat soubory s dalšími příponami v souboru bez dalšího rozšíření. Další rozšíření se může vyskytovat jenom na konci úplného názvu souboru.

Uvažujte následující příklad:

![Příklady pravidel addedExtension](media/filenesting_addedextension.png) ![Příklad efektu addedExtension](media/filenesting_addedextension_effect.png)

* *file.html. CSS* je vnořen do *file.html* kvůli **addedExtension** pravidlu.

> [!NOTE]
> Pro toto pravidlo neurčíte žádné přípony souborů `addedExtension` . ta se automaticky použije pro všechny přípony souborů. To znamená, že libovolný soubor se stejným názvem a příponou jako jiný soubor a další rozšíření na konci jsou vnořeny do druhého souboru. Nemůžete omezit efekt tohoto poskytovatele na jenom konkrétní přípony souborů.

### <a name="the-pathsegment-provider"></a>Poskytovatel pathSegment

Tento zprostředkovatel vnořovat soubory s dalšími příponami v souboru bez dalšího rozšíření. Další rozšíření se může vyskytovat pouze uprostřed úplného názvu souboru.

Uvažujte následující příklad:

![Příklady pravidel pathSegment](media/filenesting_pathsegment.png) ![Příklad efektu pathSegment](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* je v rámci *jquery.js* vnořený kvůli **pathSegment** pravidlu.

> [!NOTE]
> - Pokud neurčíte žádné konkrétní přípony souborů pro toto `pathSegment` pravidlo, bude se vztahovat na všechny přípony souborů. To znamená, že všechny soubory se stejným názvem a příponou jako jiný soubor a další rozšíření uprostřed jsou vnořeny do druhého souboru.
> - Účinek `pathSegment` pravidla na konkrétní přípony souborů můžete omezit tak, že je zadáte následujícím způsobem:
>
>    ```json
>    "pathSegment": {
>       "add": {
>         ".*": [
>           ".js",
>           ".css",
>           ".html",
>           ".htm"
>         ]
>       }
>    }
>    ```

### <a name="the-allextensions-provider"></a>Poskytovatel allExtensions

Tento zprostředkovatel vám umožní definovat pravidla vnořování souborů pro soubory s libovolnou příponou, ale stejný základní název souboru. Uvažujte následující příklad:

![Příklady pravidel allExtensions](media/filenesting_allextensions.png) ![Příklad efektu allExtensions](media/filenesting_allextensions_effect.png)

* *template.cs* a *template.doc* jsou vnořené v *template.TT* v důsledku pravidla **allExtensions** .

### <a name="the-filetofile-provider"></a>Poskytovatel fileToFile

Tento zprostředkovatel vám umožní definovat pravidla vnořování souborů na základě celých názvů souborů. Uvažujte následující příklad:

![Příklady pravidel fileToFile](media/filenesting_filetofile.png) ![Příklad efektu fileToFile](media/filenesting_filetofile_effect.png)

* *. bowerrc* je na základě pravidla **fileToFile** vnořen do *bower.js* .

### <a name="rule-order"></a>Pořadí pravidel

Řazení je důležité v každé části souboru s vlastním nastavením. Pořadí, ve kterém se pravidla spouštějí, můžete změnit přesunutím nahoru nebo dolů v uzlu **dependentFileProvider** . Například pokud máte jedno pravidlo, které vytváří **file.js** nadřazeným **souborem. TS** a jiné pravidlo, které provádí **soubor. káva** nadřazeným souborem **. TS**, pořadí, ve kterém se zobrazí v souboru, určuje chování vnoření, když jsou k dispozici všechny tři soubory. Vzhledem k tomu, že **soubor. TS** může mít pouze jednu nadřazenou položku, přičemž pravidlo provede první službu WINS.

Řazení je také důležité pro samotné oddíly pravidel, nikoli jenom pro soubory v rámci oddílu. Jakmile se dvojice souborů shoduje s pravidlem pro vnořování souborů, ignorují se další pravidla v souboru a další dvojice souborů se zpracuje.

### <a name="file-nesting-button"></a>Tlačítko pro vnořování souborů

Přes stejné tlačítko v **Průzkumník řešení** můžete spravovat všechna nastavení, včetně vlastních nastavení.

![Aktivovat vlastní pravidla vnořování souborů](media/filenesting_activatecustom.png)

## <a name="create-project-specific-settings"></a>Vytvořit nastavení specifické pro projekt

Nastavení specifická pro konkrétní řešení a projekt můžete vytvořit pomocí nabídky po kliknutí pravým tlačítkem myši (místní nabídka) každého řešení a projektu:

![Pravidla vnoření řešení a specifické pro projekt](media/filenesting_solutionprojectspecific.png)

Nastavení specifická pro řešení a specifické pro projekt jsou kombinována s aktivním nastavením sady Visual Studio. Například je možné, že máte prázdný soubor nastavení specifický pro projekt, ale **Průzkumník řešení** stále vnořování souborů. Chování vnořování probíhá buď z nastavení specifického pro řešení, nebo z nastavení sady Visual Studio. Priorita pro sloučení nastavení vnořování souborů je: Visual Studio > řešení > projektu.

Můžete říct, že Visual Studio bude ignorovat nastavení specifická pro řešení a projekt, i když soubory existují na disku, povolením možnosti **Ignorovat nastavení řešení a projektu** v části možnosti **nástrojů**  >    >  **ASP.NET Core**  >  **vnořování souborů**.

Můžete provést opak a sdělit aplikaci Visual Studio, aby používala *pouze* nastavení specifické pro řešení nebo projekt, nastavením **kořenového** uzlu na **hodnotu true**. Visual Studio ukončí slučování souborů na dané úrovni a nesloučí je se soubory vyššími než v hierarchii.

Nastavení specifické pro řešení a specifické pro projekt lze zkontrolovat do správy zdrojových kódů a celý tým, který pracuje na základu kódu, je může sdílet.

## <a name="disable-file-nesting-rules-for-a-project"></a>Zakázat pravidla vnořování souborů pro projekt

Stávající pravidla vnoření globálních souborů pro konkrétní řešení nebo projekty můžete zakázat pomocí akce **Odebrat** pro zprostředkovatele místo **Přidat**. Například pokud přidáte následující kód nastavení do projektu, jsou zakázána všechna **pathSegment** pravidla, která mohou existovat globálně pro tento konkrétní projekt:

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Viz také

- [Přizpůsobení integrovaného vývojového prostředí](../ide/personalizing-the-visual-studio-ide.md)
- [Řešení a projekty v aplikaci Visual Studio](solutions-and-projects-in-visual-studio.md)

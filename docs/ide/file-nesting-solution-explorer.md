---
title: Pravidla vnoření souborů pro Průzkumníka řešení
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jillfra
ms.openlocfilehash: a36ca2535785f72756ad66a69c2ebe4d7d5a373b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "67587029"
---
# <a name="file-nesting-in-solution-explorer"></a>Vnořování souborů v Průzkumníku řešení

**Průzkumník řešení** vnoří související soubory, aby je mohl lépe uspořádat a usnadnit jejich vyhledání. Pokud například přidáte formulář Windows Forms do projektu, soubor kódu pro formulář bude vnořen pod formulářem v **Průzkumníku řešení**. V ASP.NET základní projekty, vnoření souborů lze vzít o krok dále. Můžete si vybrat mezi přednastaveními vnoření souborů **Vypnuto**, **Výchozí**a **Web**. Můžete také [přizpůsobit vnoření souborů](#customize-file-nesting) nebo vytvořit nastavení [specifická pro řešení a konkrétní projekt](#create-project-specific-settings).

> [!NOTE]
> Tato funkce je v současné době podporována pouze pro ASP.NET základní projekty.

## <a name="file-nesting-options"></a>Možnosti vnoření souborů

![Tlačítko pro zapnutí/vypnutí vnoření souborů](media/filenesting_onoff.png)

Dostupné možnosti pro vnoření nepřizpůsobených souborů jsou:

* **Vypnuto**: Tato možnost poskytuje plochý seznam souborů bez vnoření.

* **Výchozí**: Tato možnost poskytuje výchozí chování vnoření souborů v **Průzkumníku řešení**. Pokud pro daný typ projektu neexistují žádná nastavení, nebudou vnořeny žádné soubory v projektu. Pokud existují nastavení, například pro webový projekt, bude použito vnoření.

* **Web:** Tato možnost použije chování vnoření **webového** souboru na všechny projekty v aktuálním řešení. Má mnoho pravidel a doporučujeme vám, abyste se na to podívali a řekli nám, co si myslíte. Následující snímek obrazovky zvýrazní jen několik příkladů chování vnoření souborů, které získáte s touto volbou:

   ![Vnořování souborů v Průzkumníku řešení](media/filenesting.png)

## <a name="customize-file-nesting"></a>Přizpůsobení vnoření souborů

Pokud se vám nelíbí, co dostanete out-of-the-box, můžete vytvořit vlastní, vlastní nastavení vnoření souborů, které pokyn **Průzkumníka řešení,** jak vnořit soubory. Můžete přidat libovolný počet vlastních nastavení vnoření souborů a můžete mezi nimi podle potřeby přepínat. Chcete-li vytvořit nové vlastní nastavení, můžete začít s prázdným souborem nebo můžete použít nastavení **webu** jako výchozí bod:

![Přidání vlastních pravidel vnoření souborů](media/filenesting_addcustom.png)

Jako výchozí bod doporučujeme použít nastavení **webu,** protože je snazší pracovat s něčím, co již funguje. Pokud jako výchozí bod použijete nastavení **webu,** bude soubor *.filenesting.json* vypadat podobně jako následující soubor:

![Použití existujících pravidel vnoření souborů jako základu pro vlastní nastavení](media/filenesting_editcustom.png)

Zaměřme se na **uzel dependentFileProviders** a jeho podřízené uzly. Každý podřízený uzel je typ pravidla, které visual studio můžete použít k vnoření souborů. Například **mít stejný název souboru, ale jiné rozšíření** je jeden typ pravidla. Dostupná pravidla jsou:

* **extensionToExtension**: Pomocí tohoto typu pravidla můžete soubor *soubor uhnízdit* pod *souborem File.ts*

* **fileSuffixToExtension**: Pomocí tohoto typu pravidla můžete vnořit *soubor-vsdoc.js* pod *soubor.js*

* **addedExtension**: Pomocí tohoto typu pravidla vnořte *soubor.html.css* pod *soubor.html*

* **pathSegment**: Pomocí tohoto typu pravidla vnoření *souboru jquery.min.js* pod *soubor jquery.js*

* **allExtensions**: Tento typ pravidla použijte k vnoření *souboru.* * pod *soubor.js*

* **fileToFile**: Použijte tento typ pravidla k *hnízdění bower.json* pod *.bowerrc*

### <a name="the-extensiontoextension-provider"></a>Zprostředkovatel extensionToExtension

Tento zprostředkovatel umožňuje definovat pravidla vnoření souborů pomocí konkrétních přípon souborů. Uvažujte následující příklad:

![pravidla příkladu extentionToExtension](media/filenesting_extensiontoextension.png) ![příklad extentionToExtension](media/filenesting_extensiontoextension_effect.png)

* *cart.js* je vnořen pod *cart.ts* z důvodu prvního pravidla **extensionToExtension**

* *cart.js* není vnořený pod *cart.tsx,* protože **.ts** je před **.tsx** v pravidlech a může existovat pouze jeden rodič

* *light.css* je vnořen pod *light.sass* z důvodu druhého **pravidla extensionToExtension**

* *home.html* je vnořený pod *home.md* z důvodu třetího **pravidla extensionToExtension**

### <a name="the-filesuffixtoextension-provider"></a>Zprostředkovatel fileSuffixToExtension

Tento zprostředkovatel funguje stejně jako **extensionToExtension** zprostředkovatele, s jediným rozdílem je, že pravidlo se dívá na příponu souboru namísto pouze rozšíření. Uvažujte následující příklad:

![fileSuffixToExtension příklad pravidla](media/filenesting_filesuffixtoextension.png) ![fileSuffixToExtension ukázkový efekt](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js* je vnořen pod *portal.js* z důvodu pravidla **fileSuffixToExtension**

* každý jiný aspekt pravidla funguje stejným způsobem jako **extensionToExtension**

### <a name="the-addedextension-provider"></a>Poskytovatel addedExtension

Tento zprostředkovatel vnoří soubory s další příponou pod souborem bez další přípony. Další přípona se může zobrazit pouze na konci úplného názvu souboru.

Uvažujte následující příklad:

![addedExtension example rules](media/filenesting_addedextension.png) ![addedExtension example effect efekt](media/filenesting_addedextension_effect.png)

* *soubor file.html.css* je vnořen pod *souborem file.html* z důvodu pravidla **addedExtension**

> [!NOTE]
> Nezadáte žádné přípony souborů pro `addedExtension` pravidlo; automaticky se použije na všechny přípony souborů. To znamená, že jakýkoli soubor se stejným názvem a příponou jako jiný soubor plus další přípona na konci je vnořena pod jiným souborem. Účinek tohoto zprostředkovatele nelze omezit pouze na konkrétní přípony souborů.

### <a name="the-pathsegment-provider"></a>Zprostředkovatel pathSegment

Tento zprostředkovatel vnoří soubory s další příponou pod souborbez další přípona. Další rozšíření se může zobrazit pouze uprostřed úplného názvu souboru.

Uvažujte následující příklad:

![pathSegment ukázková pravidla](media/filenesting_pathsegment.png) ![příklad segmentu cesty](media/filenesting_pathsegment_effect.png)

* *Jquery.min.js* je vnořen pod *jquery.js* z důvodu pravidla **pathSegment**

> [!NOTE]
> - Pokud pro `pathSegment` pravidlo nezadáte žádné konkrétní přípony souborů, platí pro všechny přípony souborů. To znamená, že jakýkoli soubor se stejným názvem a příponou jako jiný soubor plus další přípona uprostřed je vnořena pod jiným souborem.
> - Účinek `pathSegment` pravidla můžete omezit na konkrétní přípony souborů tak, že je určíte následujícím způsobem:
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

### <a name="the-allextensions-provider"></a>Zprostředkovatel allExtensions

Tento zprostředkovatel umožňuje definovat pravidla vnoření souborů pro soubory s libovolnou příponou, ale se stejným názvem základního souboru. Uvažujte následující příklad:

![allExtensions příklad pravidla](media/filenesting_allextensions.png) ![allExtensions ukázkový efekt](media/filenesting_allextensions_effect.png)

* *template.cs* a *template.doc* jsou vnořeny pod *template.tt* z důvodu **allExtensions** pravidlo.

### <a name="the-filetofile-provider"></a>Zprostředkovatel fileToFile

Tento zprostředkovatel umožňuje definovat pravidla vnoření souborů na základě celých názvů souborů. Uvažujte následující příklad:

![souborToFile příklad pravidla](media/filenesting_filetofile.png) ![efekt příklad souboruToFile](media/filenesting_filetofile_effect.png)

* *.bowerrc* je vnořen pod *bower.json* z důvodu **pravidla fileToFile**

### <a name="rule-order"></a>Pořadí pravidel

Řazení je důležité v každé části souboru vlastního nastavení. Můžete změnit pořadí, ve kterém jsou pravidla spouštěna jejich přesunutím nahoru nebo dolů uvnitř **uzlu dependentFileProvider.** Máte-li například jedno pravidlo, které z **souboru file.js** dělá nadřazenou položku **souboru file.ts** a jiné pravidlo, které z **mění** nadřazenou položku **file.ts**, pořadí, ve kterém se zobrazí v souboru, určuje chování vnoření, když jsou přítomny všechny tři soubory. Vzhledem k **tomu, že soubor file.ts** může mít pouze jednu nadřazenou položku, podle toho, které pravidlo provede první výhry.

Řazení je také důležité pro samotné oddíly pravidel, nejen pro soubory v rámci oddílu. Jakmile je dvojice souborů spárována s pravidlem vnoření souborů, ostatní pravidla dále v souboru jsou ignorována a další dvojice souborů je zpracována.

### <a name="file-nesting-button"></a>Tlačítko vnoření souborů

Všechna nastavení, včetně vlastních nastavení, můžete spravovat pomocí stejného tlačítka v **Průzkumníku řešení**:

![Aktivace vlastních pravidel vnoření souborů](media/filenesting_activatecustom.png)

## <a name="create-project-specific-settings"></a>Vytvoření nastavení specifického pro projekt

Nastavení specifická pro řešení a projekt můžete vytvořit pomocí nabídky po kliknutí pravým tlačítkem myši (kontextová nabídka) každého řešení a projektu:

![Pravidla vnoření specifické pro řešení a projekt](media/filenesting_solutionprojectspecific.png)

Nastavení specifická pro řešení a projekt jsou kombinována s aktivním nastavením sady Visual Studio. Můžete mít například prázdný soubor nastavení specifický pro projekt, ale **Průzkumník řešení** stále vnořuje soubory. Chování vnoření pochází z nastavení specifické pro řešení nebo nastavení sady Visual Studio. Priorita pro slučování nastavení vnoření souborů je: Visual Studio > Řešení > Project.

Aplikaci Visual Studio můžete sdělit, aby ignorovala nastavení specifická pro řešení a projekt, i když soubory existují na disku, povolením možnosti **Ignorovat nastavení řešení a projektu** v části**Možnosti** >  **nástrojů** > ASP.NET**vnoření základního****ASP.NET Core** > souboru .

Můžete provést opak a sdělit visual studio používat *pouze* nastavení specifické pro řešení nebo konkrétní projekt, nastavením **kořenového** uzlu na **hodnotu true**. Visual Studio zastaví slučování souborů na této úrovni a nekombinuje je se soubory výše v hierarchii.

Nastavení specifická pro řešení a projekt lze zkontrolovat do správy zdrojového kódu a celý tým, který pracuje na základu kódu, je může sdílet.

## <a name="disable-file-nesting-rules-for-a-project"></a>Zakázání pravidel vnoření souborů pro projekt

Existující globální pravidla vnoření souborů pro konkrétní řešení nebo projekty můžete zakázat pomocí akce **odebrání** pro zprostředkovatele namísto **přidání**. Pokud například přidáte do projektu následující kód nastavení, budou zakázána všechna pravidla **pathSegment,** která mohou existovat globálně pro tento konkrétní projekt:

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Viz také

- [Přizpůsobení prostředí IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Řešení a projekty v sadě Visual Studio](solutions-and-projects-in-visual-studio.md)

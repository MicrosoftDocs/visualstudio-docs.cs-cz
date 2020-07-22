---
title: Aktualizace sady Visual Studio s minimálním offline rozložením
description: Naučte se aktualizovat Visual Studio pomocí minimálního offline rozložení.
ms.date: 07/21/2020
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 849cad46463ffb52e2f4f2a930f05daf66f7d737
ms.sourcegitcommit: 363f3e6e30dd54366ade0d08920755da5951535c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86869878"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>Aktualizace sady Visual Studio s minimálním offline rozložením

Pro počítače, které nejsou připojené k Internetu, je vytvoření minimálního rozložení nejjednodušší a nejrychlejší způsob aktualizace offline instancí sady Visual Studio.

Nástroj pro minimální rozložení generuje rozložení, které se přizpůsobí konkrétně potřebám vašeho týmu. Podnikoví správci můžou pomocí tohoto nástroje vytvořit rozložení aktualizací pro většinu verzí sady Visual Studio 2017 a 2019. Na rozdíl od úplného rozložení sady Visual Studio obsahuje minimální rozložení pouze aktualizované balíčky, takže je vždy menší a rychlejší pro vygenerování a nasazení. Velikost rozložení aktualizace můžete dále minimalizovat zadáním pouze požadovaných jazyků, úloh a součástí.

## <a name="how-to-generate-a-minimal-layout"></a>Generování minimálního rozložení

> [!IMPORTANT]
> V těchto pokynech se předpokládá, že jste dříve vytvořili a používali rozložení. Další informace o tom, jak to udělat, najdete v tématu [aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md) .
>
> Pro lepší porozumění životnímu cyklu sady Visual Studio se podívejte na stránku [životní cyklus a údržba produktu Visual Studio](/visualstudio/releases/2019/servicing) .
>

Tento nástroj vytvoří rozložení aktualizací pro Visual Studio 2017 (15,9) a vyšší. Rozložení se dá nasadit do počítačů v síti nebo v režimu offline, aby se aktualizovaly instance sady Visual Studio. Během [normálního vytváření rozložení](update-a-network-installation-of-visual-studio.md)se stáhnou všechny balíčky pro danou verzi. Pro opravu, odinstalaci a další standardní operace v instancích sady Visual Studio se vyžaduje vytváření normálního rozložení. Minimální rozložení stahuje pouze aktualizované balíčky, takže je menší a snazší je zkopírovat do počítačů v režimu offline.

### <a name="installing-the-minimal-layout-tool"></a>Instalace nástroje pro minimální rozložení
 
 1. Nejdřív si stáhněte nástroj pro minimální rozložení, který najdete [tady](https://aka.ms/vs/installer/minimallayout). Nezapomeňte po zobrazení výzvy zvolit možnost **Uložit** a pak vyberte **Spustit**.

     ![Uložit Nástroj pro minimální rozložení](media/save-minimal-layout.png)

 2. V dalším kroku Přijměte výzvu k řízení uživatelských účtů kliknutím na **Ano**.

     ![Přijmout řízení uživatelských účtů](media/accept-user-account-control.png)

 3. Nástroj pro minimální rozložení bude nainstalován do `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` .

### <a name="how-to-use-the-minimal-layout-tool"></a>Jak používat nástroj pro minimální rozložení

`MinimalLayout.exe`k vygenerování rozložení používá následující příkazy a možnosti. Pro spuštění tohoto nástroje je nutný alespoň jeden příkaz. Tady je postup, jak tento nástroj spustit:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Příkazy
* **Preview**: pomocí tohoto příkazu můžete zobrazit náhled toho, kolik balíčků se stáhne, a celkové místo využité k vytvoření tohoto rozložení. 
* **Vygenerovat**: Tento příkaz slouží k vygenerování minimálního rozložení pro aktualizaci sady Visual Studio.
* **Znovu vygenerovat**: pomocí tohoto příkazu můžete znovu vygenerovat rozložení pomocí existujícího souboru odpovědi na minimální rozložení. Každé minimální rozložení vytvoří `MinimalLayout.json` soubor odezvy, který obsahuje původní vstupní parametry minimálního rozložení. K opětovnému vygenerování minimálního rozložení můžete použít příkaz **znovu vygenerovat** a `MinimalLayout.json` soubor odpovědí. To je užitečné, pokud chcete vytvořit minimální rozložení nové aktualizace sady Visual Studio založené na předchozím souboru odpovědi na minimální rozložení. 
   - Pro tento příkaz `MinimalLayout.json` je vyžadována cesta k souboru z již vygenerovaného rozložení. 

        ```cmd
        MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
        ```

* **Ověřit**: pomocí tohoto příkazu určete, zda je složka rozložení poškozena.
* **Oprava**: Tento příkaz použijte k opravě poškozené složky rozložení, včetně nahrazení všech chybějících balíčků ze složky rozložení.

#### <a name="options"></a>Možnosti 

|Možnosti    |Popis    |Požadováno/volitelné |Příklad |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; adresář&gt; |Určuje adresář, ve kterém má být vytvořeno minimální rozložení offline.       |Vyžadováno        |--targetLocation c:\VSLayout\ |
|-- &lt; verze baseVersion&gt;|Od této verze se vygeneruje minimální rozložení offline.   |Vyžadováno|--baseVersion 16.4.0 |
|-- &lt; verze targetVersion&gt;|Minimální rozložení offline se vygeneruje až do této verze, včetně této.|Vyžadováno|--targetVersion 16.4.4|
|--jazyky    |Určuje jazyky, které mají být zahrnuty do minimálního offline rozložení. Je možné zadat více hodnot oddělených mezerami.    |Vyžadováno    |--jazyky en-US fr-FR |
|-- &lt; ID ProductID&gt;    |ID produktu, z něhož bude vygenerováno minimální rozložení offline <br> <ul><li>Microsoft. VisualStudio. Product. Enterprise</li><li>Microsoft. VisualStudio. Product. Professional</li><li>Microsoft. VisualStudio. Product. BuildTools</li><li>Microsoft. VisualStudio. Product. TestAgent</li><li>Microsoft. VisualStudio. Product. TestController</li><li>Microsoft. VisualStudio. Product. TeamExplorer</li></ul>|Vyžadováno|--productId Microsoft. VisualStudio. Product. Enterprise |
|--filePath    |Cesta k souboru MinimalLayout.jsv souboru z již vytvořeného rozložení. Tato možnost se používá jenom s příkazem znovu vygenerovat.     |Vyžadováno pro příkaz pro opětovné vygenerování    |--filePath C:\VSLayout\minimalLayout.jsv <br><br> **Všimněte si, že příkaz znovu vygenerovat má pouze možnost--filePath.** |
|--Přidat &lt; jednu nebo více úloh nebo ID součástí&gt;    |Určuje jedno nebo více úloh nebo ID součástí, které chcete přidat. Další součásti lze globálně přidat pomocí--includeRecommended a/nebo <br> –-includeOptional. Je možné zadat více úloh nebo ID komponent oddělené mezerou.    |Volitelné    |--Přidejte Microsoft. VisualStudio. úlohu. ManagedDesktop Microsoft. VisualStudio. reNetWeb Component. GitHub. VisualStudio. |
|--includeRecommended    |Zahrnuje Doporučené součásti pro všechny nainstalované úlohy, ale ne volitelné součásti.    |Volitelné    |Pro konkrétní zatížení: <br> --přidat Microsoft. VisualStudio. úlohu. ManagedDesktop;includeRecommended <br><br> Použití na všechny úlohy:--includeRecommended |
|--includeOptional |Zahrnuje volitelné komponenty pro všechny nainstalované úlohy, včetně doporučených komponent.    |Volitelné    |Pro konkrétní zatížení: <br>--přidat Microsoft. VisualStudio. úlohu. ManagedDesktop;includeOptional <br><br> Použití na všechny úlohy:--includeOptional |

### <a name="generating-a-minimal-layout"></a>Generování minimálního rozložení

> [!IMPORTANT]
>  V těchto pokynech se předpokládá, že jste dříve vytvořili rozložení instalace sítě. Další informace o tom, jak to udělat, najdete na stránce [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md) .

Vytvořte minimální rozložení pomocí příkazu **Generovat** pro zadaný rozsah verzí. Budete také muset znát productId, jazyky a všechny požadované úlohy. Toto minimální rozložení aktualizuje všechny instance sady Visual Studio ze základní verze na a včetně cílové verze.

Před vytvořením rozložení můžete zjistit celkovou velikost staženého a počtu balíčků obsažených pomocí příkazu **Preview** . Tento příkaz má stejné možnosti jako příkaz **Generate** a podrobnosti se zapisují do konzoly.

Pojďme si projít několik příkladů, jak zobrazit náhled, vygenerovat a znovu vygenerovat minimální rozložení:

- Tady je příklad, jak zobrazit náhled rozložení pro Visual Studio Enterprise verze 16.4.0 na 16.4.4 jenom pro angličtinu.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- Tady je postup, jak vygenerovat stejné rozložení s jedním úlohou.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- A tady je postup, jak znovu vygenerovat minimální rozložení offline pomocí existujícího souboru odpovědí. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Několik dalších příkladů pomocí příkazu **Generovat** :

- Tady je postup, jak přidat další úlohu a zahrnout jenom Doporučené balíčky. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- A konečně, tady je postup, jak do minimálního rozložení zahrnout více jazyků. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

### <a name="how-to-maintain-a-minimal-layout"></a>Jak udržovat minimální rozložení

Použijte příkazy **ověřit** a **opravit** pro zachování minimálního rozložení po jeho vytvoření. Příkaz **ověřit** určuje, jestli jsou v minimálním rozložení poškozené nebo chybějící balíčky. Pokud narazíte na problémy po spuštění příkazu **ověřit** , opravte chybějící nebo poškozené balíčky pomocí příkazu **opravit** .

- Zde je postup, jak ověřit, zda rozložení obsahuje poškozené nebo chybějící balíčky: 

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- A tady je postup, jak toto rozložení opravit:

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE] 
> Toto rozložení nelze použít k opravě instalace sady Visual Studio. Chcete-li opravit existující instanci aplikace Visual Studio, přečtěte si téma [Oprava sady Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Použití minimálního offline rozložení k aktualizaci stávající instalace sady Visual Studio

Po vygenerování minimálního rozložení můžete zkopírovat celou složku minimálního rozložení do klientského počítače. To je nutné v případě, že počítač nemá přístup do složky minimálního rozložení v původním umístění.

Přejděte do složky a Identifikujte název aplikace zaváděcího nástroje. Název aplikace zaváděcího nástroje závisí na zadané hodnotě ProductId při generování minimálního rozložení. Běžné příklady najdete v následující tabulce.

|Hodnota ProductId    |Název aplikace|
|:-----------|:------------|
|Microsoft. VisualStudio. Product. Enterprise    |vs_enterprise.exe|
|Microsoft. VisualStudio. Product. Professional    |vs_professional.exe|
|Microsoft. VisualStudio. Product. BuildTools    |vs_buildtools.exe|

Aktualizace se aplikuje na instanci sady Visual Studio ve dvou krocích. Začněte tím, že aktualizujete Instalační program pro Visual Studio a pak aktualizujete Visual Studio.

1. **Aktualizace Instalační program pro Visual Studio** 

    Spusťte následující příkaz a v `vs_enterprise.exe` případě potřeby nahraďte správným názvem aplikace zaváděcího nástroje. 

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aktualizace aplikace sady Visual Studio**

    Chcete-li aktualizovat sadu Visual Studio, je nutné zadat installPath instance sady Visual Studio, kterou chcete aktualizovat. Pokud je nainstalováno více instancí sady Visual Studio, je třeba každou z nich aktualizovat samostatně. Důrazně doporučujeme, abyste zadali `–noWeb` možnost s příkazem Update, abyste zabránili instalaci komponent, které nejsou v minimálním rozložení. Tím zabráníte tomu, abyste aplikaci Visual Studio opustili v nepoužitelném stavu.

    Spusťte následující příkaz a patřičným Nahraďte parametr příkazového řádku installPath. Nezapomeňte použít také správný název aplikace zaváděcího nástroje.

    ```cmd
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Definování nastavení v souboru odpovědí](automated-installation-with-response-file.md)
* [Řízení aktualizací pro nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
* [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)

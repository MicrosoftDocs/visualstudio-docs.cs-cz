---
title: Aktualizace sady Visual Studio s minimálním offline rozložením
description: Zjistěte, jak aktualizovat Visual Studio s minimálním offline rozložením.
ms.date: 05/18/2021
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: f3bc253f0babbc404164a9e85fda1e54ba5f5297
ms.sourcegitcommit: 0088835f22334b8fee89f8c07bb12bcdfdef1639
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2021
ms.locfileid: "110188094"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>Aktualizace sady Visual Studio s minimálním offline rozložením

Pro počítače, které nejsou připojené k internetu, je vytvoření minimálního rozložení nejjednodušším a nejrychlejším způsobem, jak aktualizovat offline Visual Studio instance.

Nástroj pro minimální rozložení vygeneruje rozložení přizpůsobené potřebám vašeho týmu. Podniková správci můžou pomocí tohoto nástroje vytvořit rozložení aktualizací pro většinu verzí pro Visual Studio 2017 a 2019. Na rozdíl od úplného Visual Studio rozložení obsahuje minimální rozložení pouze aktualizované balíčky, takže generování a nasazování je vždy menší a rychlejší. Velikost rozložení aktualizací můžete dále minimalizovat zadáním pouze požadovaných jazyků, úloh a komponent.

## <a name="how-to-generate-a-minimal-layout"></a>Jak vygenerovat minimální rozložení

> [!IMPORTANT]
> Tyto pokyny předpokládají, že jste už dříve vytvořili a použili rozložení. Další informace o tom, jak to provést, najdete na stránce Aktualizace síťové [instalace Visual Studio.](update-a-network-installation-of-visual-studio.md)
>
> Pokud chcete lépe porozumět životnímu cyklu Visual Studio, podívejte se [na Visual Studio životní cyklus a údržba](/visualstudio/releases/2019/servicing) produktu.
>

Tento nástroj vytvoří rozložení aktualizací pro Visual Studio 2017 (15.9) a novější. Rozložení je možné nasadit do počítačů v síti nebo offline, aby se Visual Studio instance. Během [normálního vytváření rozložení](update-a-network-installation-of-visual-studio.md)se stáhnou všechny balíčky pro konkrétní verzi. K opravě, odinstalaci a dalším standardním operacím na instancích služby Visual Studio rozložení. Minimální rozložení stahuje jenom aktualizované balíčky, takže je menší a snadněji se kopíruje na offline počítače.

### <a name="installing-the-minimal-layout-tool"></a>Instalace nástroje s minimálním rozložením

 1. Nejprve si stáhněte nástroj s minimálním rozložením, který najdete [tady.](https://aka.ms/vs/installer/minimallayout) Po zobrazení výzvy zvolte **Uložit** a pak vyberte **Spustit.**

     ![Uložení nástroje s minimálním rozložením](media/save-minimal-layout.png)

 2. Potom kliknutím na Ano přijměte výzvu řízení uživatelských **účtů.**

     ![Přijmout řízení uživatelských účtů](media/accept-user-account-control.png)

 3. Nástroj pro minimální rozložení bude nainstalován do `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` .

### <a name="how-to-use-the-minimal-layout-tool"></a>Jak používat nástroj pro minimální rozložení

`MinimalLayout.exe` k vygenerování rozložení používá následující příkazy a možnosti. Pro spuštění tohoto nástroje je nutný alespoň jeden příkaz. Tady je postup, jak tento nástroj spustit:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Příkazy
* **Preview**: pomocí tohoto příkazu můžete zobrazit náhled toho, kolik balíčků se stáhne, a celkové místo využité k vytvoření tohoto rozložení.
* **Vygenerovat**: Tento příkaz slouží k vygenerování minimálního rozložení pro aktualizaci sady Visual Studio.
* **Znovu vygenerovat**: pomocí tohoto příkazu můžete znovu vygenerovat rozložení pomocí existujícího souboru odpovědi na minimální rozložení. Každé minimální rozložení vytvoří `MinimalLayout.json` soubor odezvy, který obsahuje původní vstupní parametry minimálního rozložení. K opětovnému vygenerování minimálního rozložení můžete použít příkaz **znovu vygenerovat** a `MinimalLayout.json` soubor odpovědí. To je užitečné, pokud chcete vytvořit minimální rozložení nové aktualizace sady Visual Studio založené na předchozím souboru odpovědi na minimální rozložení.

   Pro tento příkaz `MinimalLayout.json` je vyžadována cesta k souboru z již vygenerovaného rozložení.

    ```cmd
    MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
    ```

* **Ověřit**: pomocí tohoto příkazu určete, zda je složka rozložení poškozena.
* **Oprava**: Tento příkaz použijte k opravě poškozené složky rozložení, včetně nahrazení všech chybějících balíčků ze složky rozložení.

::: moniker range="vs-2019"

#### <a name="options"></a>Možnosti

|Možnosti    |Description    |Požadováno/volitelné |Příklad |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; adresář&gt; |Určuje adresář, ve kterém má být vytvořeno minimální rozložení offline.       |Vyžadováno        |--targetLocation c:\VSLayout\ |
|-- &lt; verze baseVersion&gt;|Od této verze se vygeneruje minimální rozložení offline.   |Vyžadováno|--baseVersion 16.4.0 |
|--targetVersion &lt; version&gt;|Minimální offline rozložení se vygeneruje až do této verze včetně.|Vyžadováno|--targetVersion 16.4.4|
|--languages    |Určuje jazyky, které se mají zahrnout do minimálního offline rozložení. Je možné zadat více hodnot oddělených mezerami.    |Vyžadováno    |--languages en-US fr-FR |
|--productIds &lt; one or more product IDs&gt;    |ID produktů, ze kterých se bude generovat minimální offline rozložení, oddělená čárkami. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|Vyžadováno|--productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional |
|--filePath    |Cesta k souboru MinimalLayout.jsv souboru z již vytvořeného rozložení. Tato možnost se používá pouze s příkazem Regenerate (Znovu vygenerovat).     |Vyžadováno pro příkaz pro opětovné vygenerování    |--filePath C:\VSLayout\minimalLayout.jsv <br><br> **Všimněte si, že příkaz znovu vygenerovat má pouze možnost--filePath.** |
|--Přidat &lt; jednu nebo více úloh nebo ID součástí&gt;    |Určuje jedno nebo více úloh nebo ID součástí, které chcete přidat. Další součásti lze globálně přidat pomocí--includeRecommended a/nebo <br> –-includeOptional. Je možné zadat více úloh nebo ID komponent oddělené mezerou.    |Volitelné    |--Přidejte Microsoft. VisualStudio. úlohu. ManagedDesktop Microsoft. VisualStudio. reNetWeb Component. GitHub. VisualStudio. |
|--includeRecommended    |Zahrnuje Doporučené součásti pro všechny nainstalované úlohy, ale ne volitelné součásti.    |Volitelné    |Pro konkrétní zatížení: <br> --přidat Microsoft. VisualStudio. úlohu. ManagedDesktop;includeRecommended <br><br> Použití na všechny úlohy:--includeRecommended |
|--includeOptional |Zahrnuje volitelné komponenty pro všechny nainstalované úlohy, včetně doporučených komponent.    |Volitelné    |Pro konkrétní zatížení: <br>--přidat Microsoft. VisualStudio. úlohu. ManagedDesktop;includeOptional <br><br> Použití na všechny úlohy: --includeOptional |

::: moniker-end

::: moniker range="vs-2017"

#### <a name="options"></a>Možnosti

|Možnosti    |Description    |Požadováno/volitelné |Příklad |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |Určuje adresář, ve kterém chcete vytvořit minimální offline rozložení.       |Vyžadováno        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt; version&gt;|Od této verze se vygeneruje minimální offline rozložení.   |Vyžadováno|--baseVersion 15.0.0 |
|--targetVersion &lt; version&gt;|Minimální offline rozložení se vygeneruje až do této verze včetně.|Vyžadováno|--targetVersion 15.9.31|
|--languages    |Určuje jazyky, které se mají zahrnout do minimálního offline rozložení. Je možné zadat více hodnot oddělených mezerami.    |Vyžadováno    |--languages en-US fr-FR |
|--productIds &lt; one or more product IDs&gt;    |ID produktů, ze kterých se bude generovat minimální offline rozložení, oddělená čárkami. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft. VisualStudio. Product. TestController</li><li>Microsoft. VisualStudio. Product. TeamExplorer</li></ul>|Vyžadováno|--productId. Microsoft. VisualStudio. Product. Enterprise, Microsoft. VisualStudio. Product. Professional |
|--filePath    |Cesta k souboru MinimalLayout.jsv souboru z již vytvořeného rozložení. Tato možnost se používá jenom s příkazem znovu vygenerovat.     |Vyžadováno pro příkaz pro opětovné vygenerování    |--filePath C:\VSLayout\minimalLayout.jsv <br><br> **Všimněte si, že příkaz znovu vygenerovat má pouze možnost--filePath.** |
|--Přidat &lt; jednu nebo více úloh nebo ID součástí&gt;    |Určuje jedno nebo více úloh nebo ID součástí, které chcete přidat. Další součásti lze globálně přidat pomocí--includeRecommended a/nebo <br> –-includeOptional. Je možné zadat více úloh nebo ID komponent oddělené mezerou.    |Volitelné    |--Přidejte Microsoft. VisualStudio. úlohu. ManagedDesktop Microsoft. VisualStudio. reNetWeb Component. GitHub. VisualStudio. |
|--includeRecommended    |Zahrnuje Doporučené součásti pro všechny nainstalované úlohy, ale ne volitelné součásti.    |Volitelné    |Pro konkrétní zatížení: <br> --přidat Microsoft. VisualStudio. úlohu. ManagedDesktop;includeRecommended <br><br> Použití na všechny úlohy: --includeRecommended |
|--includeOptional |Zahrnuje volitelné součásti pro všechny nainstalované úlohy, včetně doporučených komponent.    |Volitelné    |Pro konkrétní úlohu: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop, includeOptional <br><br> Použití na všechny úlohy: --includeOptional |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Generování minimálního rozložení

> [!IMPORTANT]
>  Tyto pokyny předpokládají, že jste už dříve vytvořili rozložení instalace sítě. Další informace o tom, jak to udělat, najdete na stránce Vytvoření síťové [instalace Visual Studio.](create-a-network-installation-of-visual-studio.md)

Vytvořte minimální rozložení pomocí příkazu **generate** pro zadaný rozsah verzí. Budete také potřebovat znát ID produktu, jazyky a všechny požadované konkrétní úlohy. Toto minimální rozložení aktualizuje všechny instance Visual Studio ze základní verze až na cílovou verzi včetně.

Před vytvořením rozložení můžete zjistit celkovou velikost stažených souborů a počet balíčků zahrnutých pomocí příkazu **preview.** Tento příkaz má stejné možnosti jako příkaz **generate** a podrobnosti se zapisují do konzoly.

Pojďme si projít několik příkladů, jak zobrazit náhled, vygenerovat a znovu vygenerovat minimální rozložení:

::: moniker range="vs-2019"

- Nejprve tady je příklad, jak zobrazit náhled rozložení pro Visual Studio Enterprise verze 16.4.0 až 16.4.4 pouze pro angličtinu.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- Tady je postup, jak vygenerovat stejné rozložení s jednou úlohou.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- A tady je postup, jak znovu vygenerovat minimální offline rozložení pomocí existujícího souboru odpovědí.

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Několik dalších příkladů pomocí **příkazu generate:**

- Tady je postup, jak přidat další úlohu a zahrnout jenom Doporučené balíčky.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Můžete také vygenerovat minimální offline rozložení, které podporuje více produktů.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- A konečně, tady je postup, jak do minimálního rozložení zahrnout více jazyků.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

::: moniker range="vs-2017"

- Tady je příklad, jak zobrazit náhled rozložení pro Visual Studio Enterprise verze 15.0.0 na 15.9.31 jenom pro angličtinu.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
    ```

- Tady je postup, jak vygenerovat stejné rozložení s jedním úlohou.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- A tady je postup, jak znovu vygenerovat minimální rozložení offline pomocí existujícího souboru odpovědí.

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Několik dalších příkladů pomocí příkazu **Generovat** :

- Tady je postup, jak přidat další úlohu a zahrnout jenom Doporučené balíčky.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Můžete také vygenerovat minimální offline rozložení, které podporuje více produktů.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
    ```

- A konečně, tady je postup, jak do minimálního rozložení zahrnout více jazyků.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>Jak udržovat minimální rozložení

Použijte příkazy **ověřit** a **opravit** pro zachování minimálního rozložení po jeho vytvoření. Příkaz **ověřit** určuje, jestli jsou v minimálním rozložení poškozené nebo chybějící balíčky. Pokud narazíte na problémy po spuštění příkazu **ověřit** , opravte chybějící nebo poškozené balíčky pomocí příkazu **opravit** .

- Zde je postup, jak ověřit, zda rozložení obsahuje poškozené nebo chybějící balíčky:

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- A tady je postup, jak toto rozložení opravit:

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE]
> Toto rozložení nelze použít k opravě instalace sady Visual Studio. Chcete-li opravit existující instanci aplikace Visual Studio, přečtěte si téma [Oprava sady Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Použití minimálního offline rozložení k aktualizaci stávající instalace sady Visual Studio

Po vygenerování minimálního rozložení můžete zkopírovat celou složku minimálního rozložení do klientského počítače. To se vyžaduje v případě, že počítač nemá přístup ke složce s minimálním rozložením v původním umístění.

Přejděte do složky a určete název aplikace bootstrapperu. Název aplikace bootstrapperu závisí na hodnotě ProductId zadané při generování minimálního rozložení. Běžné příklady najdete v následující tabulce.

|Hodnota ProductId    |Název aplikace|
|:-----------|:------------|
|Microsoft.VisualStudio.Product.Enterprise    |vs_enterprise.exe|
|Microsoft.VisualStudio.Product.Professional    |vs_professional.exe|
|Microsoft.VisualStudio.Product.BuildTools    |vs_buildtools.exe|

Aktualizace se na instanci Visual Studio ve dvou krocích. Začněte aktualizací Instalační program pro Visual Studio a pak aktualizujte Visual Studio.

1. **Aktualizace Instalační program pro Visual Studio**

    Spusťte následující příkaz a v případě potřeby nahraďte `vs_enterprise.exe`  správným názvem aplikace bootstrapperu.

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aktualizace Visual Studio aplikace**

    Pokud chcete Visual Studio, musíte zadat installPath instance Visual Studio, kterou chcete aktualizovat. Pokud je nainstalováno Visual Studio instancí, je potřeba každou z nich aktualizovat samostatně. Důrazně doporučujeme zadat možnost pomocí příkazu update, abyste zabránili instalaci komponent, které nejsou v `–noWeb` minimálním rozložení. To vám zabrání opustit Visual Studio v nepoužitelném stavu.

    Spusťte následující příkaz a odpovídajícím způsobem nahraďte parametr příkazového řádku installPath. Nezapomeňte použít také správný název aplikace zaváděcího nástroje.

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

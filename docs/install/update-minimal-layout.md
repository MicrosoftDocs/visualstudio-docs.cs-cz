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
ms.openlocfilehash: 1c3a6254c3205038be3d56c64de091e659d2bbd5
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306732"
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

Tento nástroj vytvoří rozložení aktualizací pro Visual Studio 2017 (15.9) a novější. Rozložení je možné nasadit na počítače v síti nebo offline, aby se Visual Studio instance. Během [normálního vytváření rozložení](update-a-network-installation-of-visual-studio.md)se stáhnou všechny balíčky pro konkrétní verzi. K opravě, odinstalaci a dalším standardním operacím na instancích služby Visual Studio rozložení. Minimální rozložení stahuje jenom aktualizované balíčky, takže je menší a snadněji se kopíruje na offline počítače.

### <a name="installing-the-minimal-layout-tool"></a>Instalace nástroje s minimálním rozložením

 1. Nejprve si stáhněte nástroj s minimálním rozložením, který najdete [tady.](https://aka.ms/vs/installer/minimallayout) Po zobrazení výzvy zvolte **Uložit** a pak vyberte **Spustit.**

     ![Uložení nástroje s minimálním rozložením](media/save-minimal-layout.png)

 2. Potom kliknutím na Ano přijměte výzvu řízení uživatelských **účtů.**

     ![Přijetí řízení uživatelských účtů](media/accept-user-account-control.png)

 3. Nástroj s minimálním rozložením se nainstaluje na `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` .

### <a name="how-to-use-the-minimal-layout-tool"></a>Jak používat nástroj s minimálním rozložením

`MinimalLayout.exe` používá k vygenerování rozložení následující příkazy a možnosti. Ke spuštění nástroje se vyžaduje alespoň jeden příkaz. Nástroj spustíte takhle:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Příkazy

* **Preview:** Pomocí tohoto příkazu zobrazíte náhled, kolik balíčků se bude stahovat, a celkové místo použité k vytvoření tohoto rozložení.
* **Generovat:** Pomocí tohoto příkazu vygenerování minimálního rozložení pro aktualizaci Visual Studio.
* **Znovu vygenerovat:** Pomocí tohoto příkazu můžete znovu vygenerovat rozložení pomocí existujícího souboru s minimálním rozložením odpovědí. Každé minimální rozložení vytvoří soubor `MinimalLayout.json` odpovědi, který obsahuje původní minimální vstupní parametry rozložení. K opětovnému **vygenerování** minimálního rozložení můžete použít příkaz Regenerate (Znovu vygenerovat) a soubor `MinimalLayout.json` odpovědi. To je užitečné, pokud chcete vytvořit minimální rozložení pro novou aktualizaci Visual Studio na základě předchozího minimálního souboru odpovědí rozložení.

   Pro tento příkaz se vyžaduje cesta k souboru z už `MinimalLayout.json` vygenerované rozložení.

   ```shell
   MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
   ```

* **Ověřit:** Pomocí tohoto příkazu zjistěte, jestli je složka rozložení poškozená.
* **Oprava:** Pomocí tohoto příkazu opravte poškozenou složku rozložení, včetně nahrazení všech chybějících balíčků ze složky rozložení.

#### <a name="options"></a>Možnosti

::: moniker range=">=vs-2019"

| Možnosti                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                 | Požadováno/volitelné               | Příklad                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt; dir&gt;                        | Určuje adresář, ve kterém chcete vytvořit minimální offline rozložení.                                                                                                                                                                                                                                                                                                                                                                          | Vyžadováno                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| --baseVersion &lt; version&gt;                       | Od této verze se vygeneruje minimální offline rozložení.                                                                                                                                                                                                                                                                                                                                                                    | Vyžadováno                        | --baseVersion 16.4.0                                                                                                                                             |
| --targetVersion &lt; version&gt;                     | Minimální offline rozložení se vygeneruje až do této verze včetně.                                                                                                                                                                                                                                                                                                                                                              | Vyžadováno                        | --targetVersion 16.4.4                                                                                                                                           |
| --languages                                         | Určuje jazyky, které se mají zahrnout do minimálního offline rozložení. Je možné zadat více hodnot oddělených mezerami.                                                                                                                                                                                                                                                                                                                    | Vyžadováno                        | --languages en-US fr-FR                                                                                                                                          |
| --productIds &lt; one or more product IDs&gt;        | ID produktů, ze kterých se bude generovat minimální offline rozložení, oddělená čárkami. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul> | Vyžadováno                        | --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional                                                               |
| --filePath                                          | Cesta k souboru MinimalLayout.jsv souboru z již vytvořeného rozložení. Tato možnost se používá pouze s příkazem Regenerate (Znovu vygenerovat).                                                                                                                                                                                                                                                                                                          | Vyžaduje se pro příkaz Pro opětovné vygenerování. | --filePath C:\VSLayout\minimalLayout.json <br><br> **Všimněte si, že příkaz Regenerate přijímá jako možnost pouze --filePath.**                                      |
| --add &lt; one or more workload or component IDs&gt; | Určuje jedno nebo více ID úloh nebo komponent, které se přidávají. Další komponenty je možné přidat globálně pomocí příkazu --includeRecommended a/nebo <br> –-includeOptional. Je možné zadat více ID úloh nebo komponent oddělených mezerou.                                                                                                                                                                                                   | Volitelné                        | --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio                                        |
| --includeRecommended                                | Zahrnuje doporučené komponenty pro všechny úlohy, které jsou nainstalované, ale ne volitelné součásti.                                                                                                                                                                                                                                                                                                                                  | Volitelné                        | Pro konkrétní úlohu: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop, includeRecommended <br><br> Použití na všechny úlohy: --includeRecommended |
| --includeOptional                                   | Zahrnuje volitelné součásti pro všechny nainstalované úlohy, včetně doporučených komponent.                                                                                                                                                                                                                                                                                                                                | Volitelné                        | Pro konkrétní úlohu: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop, includeOptional <br><br> Použití na všechny úlohy: --includeOptional         |

::: moniker-end

::: moniker range="vs-2017"

| Možnosti                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                 | Požadováno/volitelné               | Příklad                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt; adresář&gt;                        | Určuje adresář, ve kterém má být vytvořeno minimální rozložení offline.                                                                                                                                                                                                                                                                                                                                                                          | Vyžadováno                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| -- &lt; verze baseVersion&gt;                       | Od této verze se vygeneruje minimální rozložení offline.                                                                                                                                                                                                                                                                                                                                                                    | Vyžadováno                        | --baseVersion 15.0.0                                                                                                                                             |
| -- &lt; verze targetVersion&gt;                     | Minimální rozložení offline se vygeneruje až do této verze, včetně této.                                                                                                                                                                                                                                                                                                                                                              | Vyžadováno                        | --targetVersion 15.9.31                                                                                                                                          |
| --jazyky                                         | Určuje jazyky, které mají být zahrnuty do minimálního offline rozložení. Je možné zadat více hodnot oddělených mezerami.                                                                                                                                                                                                                                                                                                                    | Vyžadováno                        | --jazyky en-US fr-FR                                                                                                                                          |
| --productId &lt; jedno nebo více ID produktu&gt;        | ID (y) produktů, ze kterých se vygeneruje minimální rozložení offline, oddělené čárkami. <br> <ul><li>Microsoft. VisualStudio. Product. Enterprise</li><li>Microsoft. VisualStudio. Product. Professional</li><li>Microsoft. VisualStudio. Product. BuildTools</li><li>Microsoft. VisualStudio. Product. TestAgent</li><li>Microsoft. VisualStudio. Product. TestController</li><li>Microsoft. VisualStudio. Product. TeamExplorer</li></ul> | Vyžadováno                        | --productId. Microsoft. VisualStudio. Product. Enterprise, Microsoft. VisualStudio. Product. Professional                                                               |
| --filePath                                          | Cesta k souboru MinimalLayout.jsv souboru z již vytvořeného rozložení. Tato možnost se používá jenom s příkazem znovu vygenerovat.                                                                                                                                                                                                                                                                                                          | Vyžadováno pro příkaz pro opětovné vygenerování | --filePath C:\VSLayout\minimalLayout.jsv <br><br> **Všimněte si, že příkaz znovu vygenerovat má pouze možnost--filePath.**                                      |
| --Přidat &lt; jednu nebo více úloh nebo ID součástí&gt; | Určuje jedno nebo více úloh nebo ID součástí, které chcete přidat. Další součásti lze globálně přidat pomocí--includeRecommended a/nebo <br> –-includeOptional. Je možné zadat více úloh nebo ID komponent oddělené mezerou.                                                                                                                                                                                                   | Volitelné                        | --Přidejte Microsoft. VisualStudio. úlohu. ManagedDesktop Microsoft. VisualStudio. reNetWeb Component. GitHub. VisualStudio.                                        |
| --includeRecommended                                | Zahrnuje Doporučené součásti pro všechny nainstalované úlohy, ale ne volitelné součásti.                                                                                                                                                                                                                                                                                                                                  | Volitelné                        | Pro konkrétní zatížení: <br> --přidat Microsoft. VisualStudio. úlohu. ManagedDesktop;includeRecommended <br><br> Použití na všechny úlohy:--includeRecommended |
| --includeOptional                                   | Zahrnuje volitelné komponenty pro všechny nainstalované úlohy, včetně doporučených komponent.                                                                                                                                                                                                                                                                                                                                | Volitelné                        | Pro konkrétní zatížení: <br>--přidat Microsoft. VisualStudio. úlohu. ManagedDesktop;includeOptional <br><br> Použití na všechny úlohy:--includeOptional         |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Generování minimálního rozložení

> [!IMPORTANT]
> V těchto pokynech se předpokládá, že jste dříve vytvořili rozložení instalace sítě. Další informace o tom, jak to udělat, najdete na stránce [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md) .

Vytvořte minimální rozložení pomocí příkazu **Generovat** pro zadaný rozsah verzí. Budete také muset znát productId, jazyky a všechny požadované úlohy. Toto minimální rozložení aktualizuje všechny instance sady Visual Studio ze základní verze na a včetně cílové verze.

Před vytvořením rozložení můžete zjistit celkovou velikost staženého a počtu balíčků obsažených pomocí příkazu **Preview** . Tento příkaz má stejné možnosti jako příkaz **Generate** a podrobnosti se zapisují do konzoly.

Pojďme si projít několik příkladů, jak zobrazit náhled, vygenerovat a znovu vygenerovat minimální rozložení:

::: moniker range=">=vs-2019"

* Tady je příklad, jak zobrazit náhled rozložení pro Visual Studio Enterprise verze 16.4.0 na 16.4.4 jenom pro angličtinu.

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* Tady je postup, jak vygenerovat stejné rozložení s jedním úlohou.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* A tady je postup, jak znovu vygenerovat minimální rozložení offline pomocí existujícího souboru odpovědí.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

Několik dalších příkladů pomocí příkazu **Generovat** :

* Tady je postup, jak přidat další úlohu a zahrnout jenom Doporučené balíčky.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* Můžete také vygenerovat minimální offline rozložení, které podporuje více produktů.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* A konečně, tady je postup, jak do minimálního rozložení zahrnout více jazyků.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

::: moniker range="vs-2017"

* Tady je příklad, jak zobrazit náhled rozložení pro Visual Studio Enterprise verze 15.0.0 na 15.9.31 jenom pro angličtinu.

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* Tady je postup, jak vygenerovat stejné rozložení s jedním úlohou.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* A tady je postup, jak znovu vygenerovat minimální rozložení offline pomocí existujícího souboru odpovědí.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

Několik dalších příkladů pomocí příkazu **Generovat** :

* Tady je postup, jak přidat další úlohu a zahrnout jenom Doporučené balíčky.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* Můžete také vygenerovat minimální offline rozložení, které podporuje více produktů.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* A konečně, tady je postup, jak do minimálního rozložení zahrnout více jazyků.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>Jak udržovat minimální rozložení

Použijte příkazy **ověřit** a **opravit** pro zachování minimálního rozložení po jeho vytvoření. Příkaz **ověřit** určuje, jestli jsou v minimálním rozložení poškozené nebo chybějící balíčky. Pokud narazíte na problémy po spuštění příkazu **ověřit** , opravte chybějící nebo poškozené balíčky pomocí příkazu **opravit** .

* Zde je postup, jak ověřit, zda rozložení obsahuje poškozené nebo chybějící balíčky:

  ```shell
  MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
  ```

* A tady je postup, jak toto rozložení opravit:

  ```shell
  MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
  ```

>[!NOTE]
> Toto rozložení nelze použít k opravě instalace sady Visual Studio. Chcete-li opravit existující instanci aplikace Visual Studio, přečtěte si téma [Oprava sady Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Použití minimálního offline rozložení k aktualizaci stávající instalace sady Visual Studio

Po vygenerování minimálního rozložení můžete zkopírovat celou složku minimálního rozložení do klientského počítače. To je nutné v případě, že počítač nemá přístup do složky minimálního rozložení v původním umístění.

Přejděte do složky a Identifikujte název aplikace zaváděcího nástroje. Název aplikace zaváděcího nástroje závisí na zadané hodnotě ProductId při generování minimálního rozložení. Běžné příklady najdete v následující tabulce.

| Hodnota ProductId                             | Název aplikace    |
|---------------------------------------------|---------------------|
| Microsoft. VisualStudio. Product. Enterprise   | vs_enterprise.exe   |
| Microsoft. VisualStudio. Product. Professional | vs_professional.exe |
| Microsoft. VisualStudio. Product. BuildTools   | vs_buildtools.exe   |

Aktualizace se aplikuje na instanci Visual Studio ve dvou krocích. Začněte aktualizací Instalační program pro Visual Studio a pak aktualizujte Visual Studio.

::: moniker range="vs-2017"

1. **Aktualizace Instalační program pro Visual Studio**

    Spusťte následující příkaz a v případě potřeby `vs_enterprise.exe`  nahraďte správným názvem aplikace bootstrapperu.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aktualizace Visual Studio aplikace**

    Pokud chcete Visual Studio, musíte zadat instalační_Visual Studio instance, kterou chcete aktualizovat. Pokud je nainstalováno Visual Studio instancí, je potřeba každou z nich aktualizovat samostatně. Důrazně doporučujeme zadat možnost pomocí příkazu update, abyste zabránili instalaci komponent, které nejsou v `–noWeb` minimálním rozložení. To vám zabrání opustit Visual Studio v nepoužitelném stavu.

    Spusťte následující příkaz a odpovídajícím způsobem nahraďte parametr příkazového řádku installPath. Nezapomeňte také použít správný název aplikace bootstrapperu.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

::: moniker-end

::: moniker range="vs-2019"

1. **Aktualizace Instalační program pro Visual Studio**

    Spusťte následující příkaz a v případě potřeby `vs_enterprise.exe`  nahraďte správným názvem aplikace bootstrapperu.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aktualizace Visual Studio aplikace**

    Pokud chcete Visual Studio, musíte zadat instalační_Visual Studio instance, kterou chcete aktualizovat. Pokud je nainstalováno Visual Studio instancí, je potřeba každou z nich aktualizovat samostatně. Důrazně doporučujeme zadat možnost pomocí příkazu update, abyste zabránili instalaci komponent, které nejsou v `–noWeb` minimálním rozložení. To vám zabrání opustit Visual Studio v nepoužitelném stavu.

    Spusťte následující příkaz a odpovídajícím způsobem nahraďte parametr příkazového řádku installPath. Nezapomeňte také použít správný název aplikace bootstrapperu.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise"
    ```

::: moniker-end

::: moniker range=">=vs-2022"

1. **Aktualizace Instalační program pro Visual Studio**

    Spusťte následující příkaz a v případě potřeby `vs_enterprise.exe`  nahraďte správným názvem aplikace bootstrapperu.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aktualizace Visual Studio aplikace**

    Pokud chcete Visual Studio, musíte zadat instalační_Visual Studio instance, kterou chcete aktualizovat. Pokud je nainstalováno Visual Studio instancí, je potřeba každou z nich aktualizovat samostatně. Důrazně doporučujeme zadat možnost pomocí příkazu update, abyste zabránili instalaci komponent, které nejsou v `–noWeb` minimálním rozložení. To vám zabrání opustit Visual Studio v nepoužitelném stavu.

    Spusťte následující příkaz a odpovídajícím způsobem nahraďte parametr příkazového řádku installPath. Nezapomeňte také použít správný název aplikace bootstrapperu.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise"
    ```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Jak definovat nastavení v souboru odpovědí](automated-installation-with-response-file.md)
* [Řízení aktualizací síťových nasazení Visual Studio nasazení](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio životního cyklu a údržby produktů](/visualstudio/releases/2019/servicing/)

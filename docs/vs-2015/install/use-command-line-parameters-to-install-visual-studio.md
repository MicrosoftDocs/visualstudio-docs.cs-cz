---
title: Použití parametrů příkazového řádku k instalaci sady Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a3fe0233f08f33535be4b02cc06c29d919d75169
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180253"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Instalace sady Visual Studio s použitím parametrů příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [použití parametrů příkazového řádku k instalaci sady Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio).

Při instalaci sady Visual Studio 2015 z příkazového řádku můžete použít následující parametry příkazového řádku (také se označují jako přepínače).

> [!NOTE]
> Ujistěte se, že používáte vlastní instalační program, nikoli soubor zaváděcího nástroje. Ujistěte se například, že **`vs_enterprise.exe`** místo Vs_enterprise_*GUID*. exe používáte. Instalační program si můžete stáhnout z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015).

## <a name="list-of-command-line-parameters"></a>Seznam parametrů příkazového řádku

V parametrech příkazového řádku sady Visual Studio se nerozlišují velká a malá písmena.

|Parametr|Popis|
|---------------|-----------------|
|**/?**<br /><br /> **/Help**<br /><br /> **/h**|Zobrazí parametry příkazového řádku.|
|**/AddRemoveFeatures**|Určuje, které funkce se mají přidat nebo odebrat u nainstalovaného produktu.|
|**/Adminfile.** *AdminDeployment.xml*|Nainstaluje aplikaci Visual Studio pomocí datového souboru, který jste zadali pro instalaci pro správu.|
|**/Chainingpackage** *svazek*|Určuje, který svazek řetězí tento svazek. Dá se taky použít k určení prostředí zlepšování zákazníka kohorta.|
|**/CreateAdminFile \<filename>**|Určuje umístění, kde se má vytvořit řídicí soubor, který se dá použít s/adminfile..|
|**/CustomInstallPath** *InstallationDirectory*|Nainstaluje všechny balíčky s opětovným cílem do adresáře, který určíte.|
|**/ForceRestart**|Po instalaci vždy restartuje počítač.|
|**/full**|Nainstaluje všechny funkce produktu.|
|**/InstallSelectableItems \<item name 1> [; \<item name 2> ]**|Seznam položek stromu výběru pro kontrolu na obrazovce pro výběr v průvodci instalačním programem.|
|**/l**<br /><br /> **/Log** – *název souboru*|Určí umístění souboru protokolu.|
|**/layout** *adresář* /layout|Zkopíruje soubory z instalačního média do zadaného adresáře.|
|**/NoCacheOnlyMode**|Zabrání předběžnému naplnění mezipaměti balíčku.|
|**/NoRefresh**|Zakáže kontrolu novějších verzí tohoto produktu pro požadované nebo Doporučené aktualizované verze.|
|**/norestart**|Zabrání restartování počítače během instalace aplikace i po jejím dokončení. Návratové kódy, které se mají hledat, najdete v části návratové kódy v [příručce pro správce sady Visual Studio](../install/visual-studio-administrator-guide.md) .|
|**/noweb**|Zabrání instalaci z internetu.|
|**/OverrideFeedUri \<path to feed file>**|Cesta k místnímu externímu informačnímu kanálu s popisem softwarových položek|
|**/ProductKey**<br /><br /> *ProductKey*|Nastaví vlastní kód Product Key, který neobsahuje pomlčky a maximálně 25 znaků.|
|**/PromptRestart**|Vyzve uživatele před restartováním počítače.|
|**parametr**<br /><br /> **parametr**<br /><br /> **parametr**<br /><br /> **/silent**|Potlačí zobrazení uživatelského rozhraní (UI) pro instalaci aplikace. Pokud nezadáte žádné parametry s výjimkou tohoto a sada Visual Studio je již nainstalována, instalace aplikace bude spuštěna v režimu údržby.|
|**/QB**<br /><br /> **/passive**|Zobrazí průběh, ale nečeká na vstup uživatele.|
|**/Repair**|Opraví aplikaci Visual Studio.|
|**/SuppressRefreshPrompt**|Znemožní v Průvodci instalací zobrazit dialog dostupné aktualizace, takže Průvodce instalací automaticky přijme všechny požadované nebo Doporučené aktualizované verze.|
|**přepínač**<br /><br /> **/Uninstall**|Odinstaluje se [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|**/Uninstall/Force**<br /><br /> **/u/Force**|Odinstaluje Visual Studio a všechny funkce, které jsou sdíleny s jinými produkty. **Upozornění:**  Pokud použijete tento parametr, jiné produkty, které jsou nainstalovány ve stejném počítači, mohou přestat fungovat správně.|

## <a name="see-also"></a>Viz také

- [Příručka pro správce sady Visual Studio](../install/visual-studio-administrator-guide.md)
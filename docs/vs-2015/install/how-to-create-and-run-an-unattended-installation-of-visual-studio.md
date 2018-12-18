---
title: 'Postupy: vytvoření a spuštění bezobslužné instalaci | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: bc1a6ba1a36dd7514257fcbb8ba4c26ca1ee6116
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065516"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Postupy: Vytvoření a spuštění bezobslužné instalace sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spuštěním instalační aplikace sady [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jako bezobslužnou (se přizpůsobenou tichou) instalaci přes intranet namísto z média, jako je například DVD. Toto téma popisuje postup přípravy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro tento typ instalace ze sdílené síťové složky.

## <a name="creating-a-network-image"></a>Vytvoření bitové kopie v síti
 Nejprve vytvořte bitová kopie v síti [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] média.

#### <a name="to-create-a-network-image"></a>K vytvoření bitové kopie v síti

1.  Vytvořte složku na serveru (například *jednotka*: \IDEinstall\\).

2.  Stažení instalačního programu z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)a pak spusťte *produktu*.exe/Layout *jednotka*: \IDEinstall\

3.  Nasdílejte složku IDEinstall v síti a potom nastavte příslušná bezpečnostní nastavení.

     Síťová cesta instalační aplikace sady [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se podobá \\ \\ *ServerName*\IDEinstall\\*produktu*.exe.

    > [!NOTE]
    >  Instalace může selhat, pokud libovolnou kombinaci název a cesta k souboru je delší než 260 znaků. Maximální délka cesty v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je 221 znaků.  Název místní cesty by neměl přesáhnout 70 znaků a název síťové cesty by neměl překročit 39 znaků.

     Instalace může rovněž selhat, pokud názvy složek v cestě obsahují vložené mezery (například "\\\\*ServerName*\IDE instalace" nebo \\ \\ *ServerName*\Visual studio\\).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Nasazení sady Visual Studio v bezobslužném režimu
 K nasazení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v bezobslužném režimu, je třeba upravit soubor AdminDeployment.xml. Chcete-li to provést, musíte nejprve vytvořit soubor AdminDeployment.xml pomocí `/CreateAdminFile`  *\<umístění souboru >* parametr příkazového řádku. Potom tento soubor můžete použít k vložení nasazení systému Visual Studio do vaší sítě nebo stáhnout do instalace, jestliže je tento soubor *jednotka*: \IDEinstall\packages adresáře. Soubor AdminDeployment.xml není jedinečný operační systém, architekturu, edice sady Visual Studio nebo jazyk operačního systému.

> [!CAUTION]
>  V některých případech není nainstalována v soubor AdminDeployment.xml uvedeny jako vybrané položky. Pokud chcete tento problém vyřešit, umístěte položky označené jako "vybrané ="yes"" na **end** AdminDeployment.xml souboru.
>
>  Pokud nechcete instalovat volitelné závislosti položku, musíte nejprve vybrat nadřazený a zrušte označení volitelné závislosti po nadřazeným prvkem, jak je znázorněno na následujícím snímku obrazovky:
>
>  ![Instalace položek na konci soubor AdminDeployment.xml](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
>  Dalším způsobem, jak to provést, je jednoduše vynechejte volitelné podřízené objekty nadřazeného – jinými slovy, nesmí obsahovat žádný "vybrané ="no"" položky – ale přesto musíte umístit všechny "vybrané ="yes"" položky na konci soubor AdminDeployment.xml.

> [!IMPORTANT]
>  Během instalace se počítač automaticky restartuje jednou nebo vícekrát. Po restartování, je nutné se přihlásit pod stejným uživatelským účtem, pomocí kterého byl použit k provedení instalace před restartováním počítače. Automatické restartování můžete vyhnout instalací nezbytných komponent před spuštěním bezobslužné instalace. Další informace najdete v oddílu s názvem "Vyhnout se restartování během instalace" v [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).

 Schéma souboru AdminDeployment obsahuje následující prvky:

|Prvek|Atribut|Hodnoty|Popis|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Cesta*|Se chová stejně jako přepsání cesty v uživatelském rozhraní instalační aplikace. Tento prvek je ignorován, pokud již nainstalované sady Visual Studio.|
|BundleCustomizations|NoWeb|Ano&#124;výchozí|Pokud tento prvek hodnotu Ano, nebude se instalační aplikace se pokusí přejít na web průběhu instalace.|
|SelectableItemCustomization|Hidden|Ano&#124;ne|Pokud je hodnota tohoto prvku Ano, skryje vybrání volitelné položky ve stromové struktuře úprav.|
|SelectableItemCustomization|Vybrané|Ano&#124;ne|Vybere nebo zruší vybrání volitelné položky ve stromové struktuře úprav.|
|BundleCustomizations|informační kanál|Cesta|Umístění informačního kanálu, který chce uživatel použít.  Tento kanál se používá pro následné upravit operací na počítači ("Výchozí" ve výchozím nastavení).|
|BundleCustomizations|SuppressRefreshPrompt|Ano&#124;výchozí|Zabrání uživateli se zobrazí výzva k aktualizaci instalace, pokud je k dispozici novější.|
|BundleCustomizations|NoRefresh|Ano&#124;výchozí|Instalační program nebude aktualizovat, pokud není k dispozici novější verzí.|
|BundleCustomizations|NoCacheOnlyMode|Ano&#124;výchozí|Zabrání předběžnému naplnění mezipaměti balíčku.|

> [!WARNING]
>  Instalační aplikace bude respektovat stav výběru položky SelectableItem, i když je skrytý. Například pokud chcete volitelná položka vždy nainstalována, můžete ji označit jako skrytou a vybranou.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Vytvoření bezobslužné instalace sady Visual Studio

1.  V *jednotka*: \IDEinstall\AdminDeployment.xml změňte hodnotu atributu NoWeb prvku BundleCustomizations z "Výchozí" na "Ano", jak ukazuje následující příklad:

     Změna `<BundleCustomizations TargetDir="default" NoWeb="default"/>` do `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2.  Změňte atribut SelectableItemCustomization pro volitelné součásti potřeby a pak soubor uložte.

## <a name="running-unattended-setup"></a>Spuštění bezobslužné instalace
 Můžete bezobslužnou instalaci lze spustit buď automatickým spuštěním instalační aplikace sady Visual Studio na klientském počítači nebo povolením uživatelského spuštění aplikace předem definovanými nastaveními, které definujete.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Spuštění bezobslužné instalace na klientském počítači

- Otevřít **Start** nabídce zvolte **spustit**a pak zadejte \\ \\ *ServerName*\IDEinstall\vs_*produktu*parametru/adminfile .exe *PathOfTheAdmindeployment.xmlFile*<em>AdditionalParametersAsNeeded</em>

   Můžete například zadat následující příkazový řádek: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Povolení manuální instalace sady Visual Studio s předdefinovanými nastaveními

1.  Zkopírujte upravený soubor AdminDeployment.xml do sdílené síťové složce, která je jen pro čtení (například \\ \\ *ServerName*\IDEinstall\packages\AdminDeployment.xml).

2.  Povolte uživatelům instalovat z této sdílené složky.

## <a name="maintaining-an-installation"></a>Údržba instalace
 Pokud otevřete **ovládací panely** a znovu spusťte instalaci aplikace, můžete upravit funkce sady Visual Studio, odinstalovat programovací jazyky a opravit nebo odinstalovat Visual Studio.

> [!NOTE]
>  Přihlašovací údaje pro správu musí mít v místním počítači pro použití režimu údržby.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Údržba instalace na klientském počítači

-   Otevřít **ovládací panely**a klikněte na tlačítko **programy a funkce**.

-   Zvolte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]a klikněte na tlačítko **změnu**.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Chcete-li změnit nastavení AdminDeployment na klientském počítači po instalaci sady Visual Studio

1. Podle potřeby aktualizujte AdminDeployment.xml.

2. Otevřít **Start** nabídky a klikněte na tlačítko **spustit**.

3. Zadejte následující text: \\ \\ *ServerName*\IDEinstall\vs_*produktu*.exe parametru/adminfile PathToAdmindeployment.xml souboru

    AdditionalParametersAsNeeded

    Můžete například zadat následující příkazový řádek: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   Oprava je výchozím parametrem po instalaci sady Visual Studio. Pokud opravíte systém Visual Studio s aktualizované parametru/adminfile, přepíšete aktuální nastavení nasazení správy s těmi, které aktualizovaný soubor AdminDeployment.xml vyvolá.

## <a name="updating-an-installation"></a>Aktualizace instalace
 Společnost Microsoft vydala několik aktualizací do sady Visual Studio 2015. Tato část vysvětluje, jak aktualizovat vaše image bezobslužné instalace sady Visual Studio 2015 tak, že obsahují aktualizace.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Chcete-li aktualizovat bezobslužné instalace sady Visual Studio

1. Vyhledejte soubor Product.exe v existující obrazu sítě, pravým tlačítkem myši a potom klikněte na tlačítko **vlastnosti**.

2. Klikněte na tlačítko **podrobnosti** kartu a potom poznamenejte **verze produktu** vlastnost.

    ![Příklad dialogové okno Vlastnosti při bezobslužné instalaci sady Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "bezobslužné instalace – dialogové okno Vlastnosti")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Pokud je verze produktu 14.0.24720.0 nebo 14.0.24720.1, postupujte podle těchto kroků:
4. 1.  Spustit *Product.exe* /Layout *jednotka:* \IDEinstall na počítači, který má přístup k Internetu. (Například spusťte: `vs_enterprise.exe /Layout d:\IDEinstall`.)

   2.  Po dokončení / layout kopírovat nové image do nového umístění.

   3.  Vytvořit a upravit soubor AdminDeployment.xml. Chcete-li to provést, použijte `/CreateAdminFile`  *\<umístění souboru >* parametr příkazového řádku. (Další informace najdete v tématu "Nasazení sady Visual Studio v bezobslužném režimu" části tohoto článku.)

   4.  Na klientském počítači a spusťte následující příkaz k aktualizaci kopie sady Visual Studio, který jste dříve nainstalovali: "\\\\*server1*\IDEinstall_Updated_1\\*Product.exe*  parametru/adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart / ".

        Například spusťte: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>Další hodnoty verze produktu postupujte podle těchto kroků:
6. 1.  Spustit *Product.exe* /Layout *jednotka:* \IDEinstall na počítači, který má přístup k Internetu. (Například spustit `vs-enterprise.exe /Layout d:\IDEinstall`.)

   2.  Po dokončení / layout kopírovat nové image do nového umístění. (Nebo, místo toho můžete přepsat existující obrazu sítě).

   3.  Vytvořit a následně upravit soubor AdminDeployment.xml. Chcete-li to provést, použijte `/CreateAdminFile`  *\<umístění souboru >* parametr příkazového řádku. (Další informace najdete v tématu "Nasazení sady Visual Studio v bezobslužném režimu" části tohoto článku.)

   4.  Pokud zkopírujete bitovou kopii do nového umístění, musíte spustit následující příkaz v klientském počítači. Chcete-li aktualizovat kopii sady Visual Studio, který jste dříve nainstalovali: "\\\\*server1*\IDEinstall_Updated_1\\ *Product.exe* parametru/adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart / ".

        Například spusťte: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5.  Pokud přepíšete existující obrazu sítě, můžete spustit příkaz, jak je uvedeno v předchozím kroku, nebo můžete postupovat takto:

   6.  1.  Otevřít **ovládací panely**a klikněte na tlačítko **programy a funkce**.

       2.  Zvolte **sady Visual Studio**a klikněte na tlačítko **změnu**.

       3.  Po spuštění sady Visual Studio v režimu údržby, klikněte na tlačítko **změnit**.

       4.  Nejnovější aktualizace by se zobrazit na stránce funkce. Vyberte funkce, které chcete nainstalovat, klikněte na tlačítko **Další**a potom klikněte na tlačítko **aktualizovat** instalace aktualizace a nové funkce.

## <a name="registering-the-product"></a>Registrace produktu
 Po dokončení instalace můžete zaregistrovat svou kopii [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zevnitř [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

#### <a name="to-register"></a>K registraci

1.  Otevřít **pomáhají** nabídky a klikněte na tlačítko **registrovat produkt**.

2.  Zadejte kód product key.

     (Další informace najdete v tématu [postupy: Vyhledání kódu Product Key sady Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) a [postupy: automatické použití kódů product key při nasazení sady Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md) témata.)

## <a name="see-also"></a>Viz také
 [Instalace sady Visual Studio](../install/install-visual-studio-2015.md)
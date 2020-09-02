---
title: 'Postupy: vytvoření a spuštění bezobslužné instalace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 26e059d4fdc8eadd422924dd6bbda6f7c945ccfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833482"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Postupy: Vytvoření a spuštění bezobslužné instalace sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Instalaci instalační aplikace můžete spustit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jako bezobslužnou (tj. přizpůsobenou tichou) instalaci prostřednictvím intranetu místo z média, jako je například DVD. Toto téma popisuje, jak připravit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tento typ instalace ze sdílené síťové složky.

## <a name="creating-a-network-image"></a>Vytvoření bitové kopie sítě
 Nejprve vytvořte síťovou bitovou kopii [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] média.

#### <a name="to-create-a-network-image"></a>Vytvoření bitové kopie sítě

1. Vytvořte na serveru složku (například *Drive*: \IDEinstall \\ ).

2. Stáhněte instalační program z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)a potom spusťte *produkt*. exe/layout *Drive*: \IDEinstall\

3. Nasdílejte složku IDEinstall v síti a pak nastavte příslušná nastavení zabezpečení.

     Síťová cesta instalační aplikace se [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podobá \\ \\ *serveru ServerName*\IDEinstall \\ *Product*. exe.

    > [!NOTE]
    > Instalace může selhat, pokud libovolná kombinace cesty a názvu souboru překračuje 260 znaků. Maximální délka cesty v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je 221 znaků.  Název místní cesty by neměl být delší než 70 znaků a název síťové cesty by neměl být delší než 39 znaků.

     Instalace může selhat i v případě, že názvy složek v cestě obsahují vložené mezery (například " \\ \\ *servername*\IDE Install" nebo \\ \\ *servername*\Visual Studio \\ ).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Nasazení sady Visual Studio v bezobslužném režimu
 Chcete-li nasadit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v bezobslužném režimu, je třeba upravit soubor AdminDeployment.xml. Chcete-li to provést, musíte nejprve vytvořit soubor AdminDeployment.xml pomocí `/CreateAdminFile` *\<file location>* parametru příkazového řádku. Pak můžete tento soubor použít buď k odeslání nasazení sady Visual Studio do vaší sítě, nebo k instalaci do instalace, pokud tento soubor vložíte do složky *jednotka*: \IDEinstall\packages. AdminDeployment.xml soubor není jedinečný pro operační systém, architekturu, edici sady Visual Studio ani jazyk operačního systému.

> [!CAUTION]
> V některých případech se v souboru AdminDeployment.xml neinstalují položky uvedené jako vybrané. Chcete-li vyřešit tento problém, umístěte položky označené "Selected =" Yes "" na **konci** souboru AdminDeployment.xml.
>
> Pokud nechcete instalovat volitelné závislosti položky, musíte nejprve vybrat nadřazenou položku a pak zrušit výběr volitelných závislostí po nadřazeném prvku, jak je znázorněno na následujícím snímku obrazovky:
>
> ![Položky instalace na konci souboru AdminDeployment.xml](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
> Dalším způsobem, jak to provést, je jednoduše vynechat volitelné podřízené objekty nadřazeného objektu – jinými slovy neobsahují žádné položky "Selected =" ne "", ale stále je nutné umístit všechny položky "Selected =" Ano "" na konci AdminDeployment.xml souboru.

> [!IMPORTANT]
> Během instalace může počítač jednou nebo vícekrát automaticky restartovat počítač. Po restartování se musíte přihlásit pomocí stejného uživatelského účtu, ke kterému jste se přihlásili, abyste instalaci mohli provést před restartováním počítače. Automatickému restartování se můžete vyhnout tak, že před spuštěním bezobslužné instalace nainstalujete požadované součásti. Další informace najdete v části s názvem "Vyhněte se restartování během instalace" v [příručce pro správce sady Visual Studio](../install/visual-studio-administrator-guide.md).

 Schéma souboru AdminDeployment obsahuje následující prvky:

|Prvek|Atribut|Hodnoty|Popis|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Cesta*|Se chová stejně jako přepsání cesty v uživatelském rozhraní instalační aplikace. Tento prvek je ignorován, pokud je již nainstalována aplikace Visual Studio.|
|BundleCustomizations|NoWeb|Ano&#124;výchozí|Pokud je hodnota tohoto prvku Ano, instalační aplikace se nikdy během akce instalace nepokusí přejít na web.|
|SelectableItemCustomization|Skrytý|Ano&#124;ne|Pokud je hodnota tohoto prvku Ano, skrývá položku s možností výběru v rámci stromu přizpůsobení.|
|SelectableItemCustomization|Vybráno|Ano&#124;ne|Vybere nebo zruší výběrovou položku ve stromu přizpůsobení.|
|BundleCustomizations|Informační kanál|Cesta|Umístění informačního kanálu, který chce uživatel použít.  Tento informační kanál se používá pro následné operace úprav na počítači (výchozí nastavení).|
|BundleCustomizations|SuppressRefreshPrompt|Ano&#124;výchozí|Zabrání uživateli v zobrazení výzvy k aktualizaci instalačního programu, pokud je k dispozici novější.|
|BundleCustomizations|Aktualizovat|Ano&#124;výchozí|Instalaci nelze aktualizovat, pokud je k dispozici novější.|
|BundleCustomizations|NoCacheOnlyMode|Ano&#124;výchozí|Zabrání předběžnému naplnění mezipaměti balíčku.|

> [!WARNING]
> Instalační aplikace bude respektovat vybraný stav SelectableItem, i když je skrytý. Například pokud chcete, aby se vybraná položka vždy nainstalovala, můžete ji označit jako skrytou a vybranou.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Vytvoření bezobslužné instalace sady Visual Studio

1. V souboru:\IDEinstall\AdminDeployment.xml *jednotky* změňte hodnotu atributu NoWeb elementu BundleCustomizations z "default" na "Yes", jak ukazuje následující příklad:

     Změnit `<BundleCustomizations TargetDir="default" NoWeb="default"/>` na `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2. Změňte atribut SelectableItemCustomization podle potřeby pro volitelné součásti a pak soubor uložte.

## <a name="running-unattended-setup"></a>Spuštění bezobslužné instalace
 Bezobslužnou instalaci lze spustit buď automaticky spuštěním instalační aplikace sady Visual Studio na klientských počítačích, nebo povolením, aby uživatelé aplikaci spustili sami pomocí nastavení, které definujete.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Spuštění bezobslužné instalace na klientském počítači

- Otevřete nabídku **Start** , zvolte příkaz **Spustit**a pak zadejte \\ \\ *servername*\IDEinstall\ vs_*produkt*. exe/adminfile. *PathOfTheAdmindeployment.xmlFile*<em>AdditionalParametersAsNeeded</em>

   Můžete například zadat následující příkazový řádek: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Povolení ruční instalace sady Visual Studio s předdefinovanými nastaveními pro klienty

1. Zkopírujte přizpůsobený AdminDeployment.xml soubor do sdílené síťové složky, která je jen pro čtení (například \\ \\ *servername*\IDEinstall\packages\AdminDeployment.xml).

2. Umožněte uživatelům instalovat z této sdílené složky.

## <a name="maintaining-an-installation"></a>Údržba instalace
 Pokud otevřete **Ovládací panely** a znovu spustíte instalační aplikaci, můžete upravit funkce sady Visual Studio, odinstalovat programovací jazyky a opravit nebo odinstalovat sadu Visual Studio.

> [!NOTE]
> Chcete-li použít režim údržby, musíte mít v místním počítači pověření správce.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Údržba instalace na klientském počítači

- Otevřete **Ovládací panely**a zvolte **programy a funkce**.

- Zvolte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a pak zvolte **změnit**.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Změna nastavení AdminDeployment v klientském počítači po instalaci sady Visual Studio

1. Aktualizujte AdminDeployment.xml podle potřeby.

2. Otevřete nabídku **Start** a poté zvolte možnost **Spustit**.

3. Zadejte následující text: \\ \\ *servername*\IDEinstall\ vs_*Product*. exe/adminfile. PathToAdmindeployment.xml File

    AdditionalParametersAsNeeded

    Můžete například zadat následující příkazový řádek: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   Oprava je výchozím parametrem po instalaci sady Visual Studio. Pokud provádíte opravu sady Visual Studio s aktualizovaným/adminfile., přepíšete aktuální nastavení nasazení správce pomocí těch, které se v aktualizovaném souboru AdminDeployment.xml vyvolá.

## <a name="updating-an-installation"></a>Aktualizace instalace
 Společnost Microsoft vydala několik aktualizací sady Visual Studio 2015. V této části se dozvíte, jak aktualizovat bitovou kopii sady Visual Studio 2015 s bezobslužnou instalací, aby obsahovala aktualizace.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Aktualizace bezobslužné instalace sady Visual Studio

1. Vyhledejte soubor Product.exe v existující imagi sítě, klikněte na něj pravým tlačítkem myši a pak klikněte na **vlastnosti**.

2. Klikněte na kartu **Podrobnosti** a pak si poznamenejte vlastnost **verze produktu** .

    ![Příklad dialogového okna vlastnosti při bezobslužné instalaci sady Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "Bezobslužná instalace – dialogové okno vlastností")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Pokud je verze produktu 14.0.24720.0 nebo 14.0.24720.1, použijte následující postup:
   1. Spusťte *Product.exe* /layout *jednotka:* \IDEinstall na počítači, který má přístup k Internetu. (Například Run: `vs_enterprise.exe /Layout d:\IDEinstall` .)

   2. Po dokončení/layout zkopírujte novou image do nového umístění.

   3. Vytvořte a upravte soubor AdminDeployment.xml. K tomu použijte `/CreateAdminFile` *\<file location>* parametr příkazového řádku. (Další informace najdete v části nasazení sady Visual Studio v bezobslužném režimu v tomto článku.)

   4. Na klientském počítači spusťte následující příkaz, který aktualizuje kopii sady Visual Studio, kterou jste předtím nainstalovali: " \\ \\ *Server1*\ IDEinstall_Updated_1 \\ *Product.exe* /adminfile. \\ \server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart".

        Například spusťte: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>Pro jiné hodnoty verze produktu použijte následující postup:
   1. Spusťte *Product.exe* /layout *jednotka:* \IDEinstall na počítači, který má přístup k Internetu. (Například Run `vs-enterprise.exe /Layout d:\IDEinstall` .)

   2. Po dokončení/layout zkopírujte novou image do nového umístění. (Nebo můžete místo toho přepsat existující bitovou kopii sítě.)

   3. Vytvořte soubor AdminDeployment.xml a upravte ho. K tomu použijte `/CreateAdminFile` *\<file location>* parametr příkazového řádku. (Další informace najdete v části nasazení sady Visual Studio v bezobslužném režimu v tomto článku.)

   4. Pokud kopírujete image do nového umístění, musíte na klientském počítači spustit následující příkaz, abyste aktualizovali kopii sady Visual Studio, kterou jste předtím nainstalovali: " \\ \\ *Server1*\ IDEinstall_Updated_1 \\ *Product.exe* /adminfile. \\ \server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart".

        Například spusťte: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5. Pokud přepíšete existující bitovou kopii sítě, můžete spustit příkaz, který je uveden v předchozím kroku, nebo můžete provést následující akce:
       1. Otevřete **Ovládací panely**a zvolte **programy a funkce**.

       2. Zvolte možnost **Visual Studio**a pak zvolte možnost **změnit**.

       3. Po spuštění sady Visual Studio v režimu údržby klikněte na **Upravit**.

       4. Na stránce funkce by se měla zobrazit nejnovější aktualizace. Vyberte další funkce, které chcete nainstalovat, klikněte na tlačítko **Další**a potom kliknutím na tlačítko **aktualizovat** nainstalujte aktualizaci i nové funkce.

## <a name="registering-the-product"></a>Registrace produktu
 Po dokončení instalace můžete svou kopii zaregistrovat v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

#### <a name="to-register"></a>K registraci

1. Otevřete nabídku **help** a zvolte možnost **Registrovat produkt**.

2. Zadejte kód Product Key.

     (Další informace naleznete v tématu [Postupy: vyhledání kódu Product Key sady Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) a [Postupy: automatické použití kódů Product Key při nasazení témat sady Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md) .)

## <a name="see-also"></a>Viz také
 [Instalace sady Visual Studio](../install/install-visual-studio-2015.md)
---
title: Správa odkazů v projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- Visual C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
ms.assetid: 05d1c51b-44f3-4973-8a11-6c919b08ad62
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1f2f3c26d89616f083c218c6b11610fe5e329a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651320"
---
# <a name="managing-references-in-a-project"></a>Správa odkazů v projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Před psaním kódu proti externí komponentě nebo připojené službě musí projekt nejprve obsahovat odkaz na něj. Odkaz je v podstatě záznam v souboru projektu, který obsahuje informace, které Visual Studio potřebuje k umístění komponenty nebo služby.

 Chcete-li přidat odkaz, klikněte pravým tlačítkem na uzel odkazy v Průzkumník řešení a vyberte možnost **Přidat odkaz**. Další informace najdete v tématu [Postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

 ![Přidat odkaz v jazyce Visual C&#43;&#43;](../ide/media/vs2015-cpp-add-reference.png "vs2015_cpp_add_reference")

 Můžete vytvořit odkaz na následující typy komponent/služeb:

- Odkazy na aplikace pro Windows Store

- .NET Framework knihovny tříd nebo sestavení

- COM – součásti

- Další sestavení nebo knihovny tříd projektů ve stejném řešení

- webové služby XML

## <a name="windows-store-app-references"></a>Odkazy na aplikace pro Windows Store

### <a name="project-references"></a>Odkazy na projekty
 Projekty Univerzální platforma Windows (UWP), které cílí na Windows 10, můžou vytvářet odkazy na jiné projekty UWP v řešení nebo na projekty nebo binární soubory, které cílí na Windows Store [!INCLUDE[win81](../includes/win81-md.md)] . za předpokladu, že tyto projekty nepoužívají rozhraní API, která se už nepoužívají ve Windows 10. Další informace najdete v tématu [Přesun z prostředí Windows Runtime 8 na UWP](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx).

 Pokud se rozhodnete změnit cílení [!INCLUDE[win81](../includes/win81-md.md)] projektů na Windows 10, přečtěte si téma [přenos, migrace a upgrade projektů sady Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) .

### <a name="extension-sdk-references"></a>Odkazy na sadu SDK rozšíření
 Projekty Visual Basic, C#, C++ a JavaScriptu pro Windows Store, které cílí na Univerzální platforma Windows (UWP), můžou odkazovat na rozšiřující sady SDK, které cílí [!INCLUDE[win81](../includes/win81-md.md)] , pokud tato rozšíření sady SDK nepoužívají rozhraní API, která se už nepoužívají ve Windows 10. Zkontrolujte web dodavatele rozšíření SDK, abyste zjistili, jestli na něj můžou odkazovat projekty Windows Store, které cílí na UWP.

 Pokud zjistíte, že sada SDK rozšíření, na kterou odkazuje vaše aplikace, není podporovaná, musíte provést následující kroky:

1. Podívejte se na název projektu, který způsobuje chybu. Platforma, na kterou váš projekt cílí, je uvedena v závorkách vedle názvu projektu. Například **MyProjectName (Windows 8.1)** znamená, že váš projekt **MyProjectName** je cílen na verzi platformy [!INCLUDE[win81](../includes/win81-md.md)] .

2. Přejít na web dodavatele, který vlastní nepodporovanou sadu SDK a nainstalujte verzi sady SDK rozšíření se závislostmi, které jsou kompatibilní s verzí platformy, na kterou váš projekt cílí.

    > [!NOTE]
    > Jedním ze způsobů, jak zjistit, jestli sada rozšíření SDK má závislosti na jiných rozšiřujících sadách SDK, je restartovat Visual Studio, vytvořit nový projekt C# Windows Store, kliknout pravým tlačítkem na projekt a zvolit **Přidat odkaz**, přejít na kartu **Windows** , přejít na dílčí kartu **rozšíření** , vybrat sadu SDK rozšíření a podívat se do pravého podokna ve **Správci odkazů**. Pokud mají závislosti, budou uvedeny zde.

    > [!IMPORTANT]
    > Pokud projekt cílí na Windows 10 a sada rozšíření SDK nainstalovaná v předchozím kroku má závislost na balíčku Microsoft Visual C++ Runtime, verze Microsoft Visual C++ balíčku modulu runtime, která je kompatibilní s Windows 10 je v 14.0 a je nainstalovaná se sadou Visual Studio 2015.

3. Pokud sada rozšíření SDK, kterou jste nainstalovali v předchozím kroku, má závislosti na dalších rozšířeních SDK, navštivte weby dodavatelů, kteří závislosti vlastní, a nainstalujte verze těchto závislostí, které jsou kompatibilní s verzí platformy, na kterou váš projekt cílí.

4. Restartujte Visual Studio a otevřete svoji aplikaci.

5. Klikněte pravým tlačítkem na uzel **odkazy** v projektu, který způsobil chybu, a vyberte **Přidat odkaz** .

6. Klikněte na kartu **Windows** a potom na dílčí kartu **rozšíření** a potom zrušte zaškrtnutí políček pro staré sady SDK rozšíření a zaškrtněte políčka pro nové sady SDK rozšíření. Klikněte na **OK**.

## <a name="adding-a-reference-at-design-time"></a>Přidání odkazu v době návrhu
 Když vytvoříte odkaz na sestavení v projektu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vyhledá sestavení v následujících umístěních:

- Aktuální adresář projektu. (Tato sestavení můžete najít pomocí karty **Procházet** .)

- Další adresáře projektu ve stejném řešení. (Tato sestavení můžete najít na kartě **projekty** .)

> [!NOTE]
> Všechny projekty obsahují implicitní odkaz na mscorlib. Visual Basic projekty obsahují implicitní odkaz na `Microsoft.VisualBasic` .
>
> Všechny projekty v aplikaci Visual Studio obsahují implicitní odkaz na `System.Core` , i když `System.Core` je odebrán ze seznamu odkazů.

## <a name="references-to-shared-components-at-run-time"></a>Odkazy na sdílené součásti za běhu
 V době běhu musí být komponenty buď ve výstupní cestě projektu, nebo v [globální mezipaměti sestavení](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC). Pokud projekt obsahuje odkaz na objekt, který není v jednom z těchto umístění, je nutné zkopírovat odkaz na výstupní cestu projektu při sestavování projektu. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A>Vlastnost označuje, zda má být tato kopie vytvořena. Pokud je hodnota **true**, odkaz je zkopírován do adresáře projektu při sestavování projektu. Pokud je hodnota **false**, odkaz není zkopírován.

 Pokud nasadíte aplikaci, která obsahuje odkaz na vlastní komponentu registrovanou v globální mezipaměti sestavení (GAC), komponenta nebude nasazena s aplikací bez ohledu na <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> nastavení. V dřívějších verzích nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jste mohli nastavit <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> vlastnost na odkaz, aby bylo zajištěno, že bylo sestavení nasazeno. Nyní je třeba ručně přidat sestavení do složky \Bin. Tím se veškerý vlastní kód uloží do kontroly a snižuje riziko publikování vlastního kódu, se kterým nejste obeznámeni.

 Ve výchozím nastavení <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> je vlastnost nastavena na **hodnotu false** , je-li sestavení nebo komponenta v globální mezipaměti sestavení (GAC) nebo je součástí rozhraní. V opačném případě je hodnota nastavena na **true**. Odkazy z projektu na projekt jsou vždy nastaveny na **hodnotu true**.

## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odkazování na projekt nebo sestavení, které cílí na jinou verzi .NET Framework
 Můžete vytvářet aplikace, které odkazují na projekty nebo sestavení, které cílí na jinou verzi .NET Framework. Můžete například vytvořit aplikaci, která cílí na sestavení, které [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] cílí na sestavení [!INCLUDE[dnprdnext](../includes/dnprdnext-md.md)] . Vytvoříte-li projekt, který se zaměřuje na starší verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , nemůžete v tomto projektu nastavit odkaz na projekt nebo sestavení, které cílí na [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] verzi nebo .NET Framework verze 4.

 Další informace najdete v tématu [cílení na konkrétní verzi .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="project-to-project-references"></a>Odkazy z projektu na projekt
 Odkazy z projektu na projekt jsou odkazy na projekty obsahující sestavení; můžete je vytvořit pomocí karty **projekt** . Visual Studio může najít sestavení, pokud je předána cesta k projektu.

 Pokud máte projekt, který vytváří sestavení, měli byste odkazovat na projekt a nepoužívat odkaz na soubor (viz níže). Výhodou odkazu typu projekt-projekt je, že vytvoří závislost mezi projekty v systému sestavení. Závislý projekt bude sestaven, pokud byl od posledního vytvoření odkazujícího projektu změněn. Odkaz na soubor nevytváří závislost sestavení, takže je možné sestavit odkazující projekt bez sestavení závislého projektu a odkaz může být zastaralý. (To znamená, že projekt může odkazovat na dříve sestavenou verzi projektu.) To může mít za následek, že v adresáři bin je vyžadováno několik verzí jediné knihovny DLL, což není možné. Když dojde ke konfliktu, zobrazí se zpráva, například [Upozornění: závislost ' soubor ' v projektu ' Project ' ' nelze zkopírovat do běhového adresáře, protože by přepsala odkaz ' File. '](../misc/warning-the-dependency-file-in-project-project-cannot-be-copied.md). Další informace najdete v tématu [řešení potíží s poškozenými odkazy](../ide/troubleshooting-broken-references.md) a [Postupy: vytvoření a odebrání závislostí projektu](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Odkaz na soubor namísto odkazu projekt-projekt je vytvořen, pokud je cílová verze .NET Framework jednoho projektu verze 4,5 a cílová verze druhého projektu je verze 2, 3, 3,5 nebo 4,0.

## <a name="file-references"></a>Odkazy na soubory
 Odkazy na soubory jsou přímé odkazy na sestavení mimo kontext projektu sady Visual Studio; můžete je vytvořit pomocí karty **Procházet** **Správce odkazů**. Odkaz na soubor použijte, pokud máte pouze sestavení nebo komponentu a nemáte projekt, který jej vytvoří jako výstup.

## <a name="see-also"></a>Viz také
 [Řešení potíží s porušeným odkazem](../ide/troubleshooting-broken-references.md) na [programování pomocí sestavení](https://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6) [Postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)

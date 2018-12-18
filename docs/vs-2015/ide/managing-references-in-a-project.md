---
title: Správa odkazů v projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 10fed2fa77274469a7b82a1583e825c57ca4a581
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195595"
---
# <a name="managing-references-in-a-project"></a>Správa odkazů v projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Předtím, než můžete napsat kód proti externí komponentě nebo připojené služby, váš projekt musí nejprve obsahovat odkaz na jeho. Odkaz je v podstatě záznam v souboru projektu, který obsahuje informace, že Visual Studio potřebuje najít komponentu nebo službu.  
  
 Přidání odkazu, klikněte pravým tlačítkem na uzel odkazy v Průzkumníku řešení a zvolte **přidat odkaz**. Další informace najdete v tématu [postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).  
  
 ![Přidání odkazu v jazyce Visual C&#43;&#43;](../ide/media/vs2015-cpp-add-reference.png "vs2015_cpp_add_reference")  
  
 Můžete vytvořit odkaz na následující typy komponent nebo služeb Team Foundation:  
  
-   Odkazy na aplikace pro Windows Store  
  
-   Knihovny tříd rozhraní .NET framework nebo sestavení  
  
-   COM – součásti  
  
-   Jiné sestavení nebo knihovny tříd projektů ve stejném řešení  
  
-   webové služby XML  
  
## <a name="windows-store-app-references"></a>Odkazy na aplikace pro Windows Store  
  
### <a name="project-references"></a>Odkazy na projekt  
 Univerzální platforma Windows (UPW) projekty, které cílí na Windows 10 můžete vytvořit odkazy na jiné projekty UWP v řešení nebo projekty Windows Store nebo binárních souborech, které se zaměřují [!INCLUDE[win81](../includes/win81-md.md)]za předpokladu, že tyto projekty nepoužívají rozhraní API, která jsou zastaralé ve Windows 10. Další informace najdete v tématu [přesunout z Windows 8 modulu Runtime pro UPW](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx).  
  
 Pokud budete chtít změnit cíl [!INCLUDE[win81](../includes/win81-md.md)] projektů pro Windows 10, najdete v článku [přenosy, migrace a upgrade projektů sady Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)  
  
### <a name="extension-sdk-references"></a>Odkazy na rozšíření SDK  
 Projekty Visual Basic, C#, C++ a JavaScript Windows Store, které používají univerzální platformu Windows (UPW) můžete odkazovat na rozšíření SDK, které se zaměřují [!INCLUDE[win81](../includes/win81-md.md)], tak dlouho, dokud tato rozšíření sady SDK nepoužívají rozhraní API, která se již nepoužívají v systému Windows 10. Zkontrolujte web dodavatele rozšíření SDK a zjistěte, zda jej lze odkazovat projekty Windows Store, které se zaměřují UPW.  
  
 Pokud zjistíte, že není podporováno rozšíření SDK, které odkazuje vaše aplikace, je nutné provést následující kroky:  
  
1.  Podívejte se na název projektu, který je příčinou chyby. Platformy, na kterou váš projekt je cílen na verzi je uvedena v závorkách vedle názvu projektu. Například **MyProjectName (Windows 8.1)** znamená, že váš projekt **MyProjectName** je zaměřen na verzi platformy [!INCLUDE[win81](../includes/win81-md.md)].  
  
2.  Přejděte na web dodavatele, který vlastní nepodporovanou sadu SDK rozšíření a nainstalujte verzi sady SDK rozšíření se závislostmi, které jsou kompatibilní s verzí platformy, na kterou váš projekt cílí.  
  
    > [!NOTE]
    >  Jedním ze způsobů a zjistěte, zda rozšíření SDK má závislosti na dalších rozšířeních SDK je restartovat aplikaci Visual Studio, vytvořte nový projekt C# Windows Store, klikněte pravým tlačítkem na projekt a zvolte **přidat odkaz**, přejděte  **Windows** záložku, přejděte **rozšíření** dílčí kartu, vyberte sadu rozšíření SDK a podívejte se na v pravém podokně **správce odkazů**. Pokud existují závislosti, budou uvedeny zde.  
  
    > [!IMPORTANT]
    >  Pokud váš projekt je cílen na verzi Windows 10 a v předchozím kroku nainstalované rozšíření SDK obsahuje závislost na balíčku Microsoft Visual C++ Runtime, verze balíčku Microsoft Visual C++ Runtime, který je kompatibilní s Windows 10 je v14.0 a je nainstalovaná pomocí sady Visual Studio 2015.  
  
3.  Pokud jste v předchozím kroku nainstalované rozšíření SDK má závislosti na dalších rozšířeních SDK, navštivte weby dodavatelů, kteří závislosti vlastní a nainstalujte verze těchto závislostí, které jsou kompatibilní s verzí platformy vaší Projekt je cílen na verzi.  
  
4.  Restartujte Visual Studio a otevřete aplikaci.  
  
5.  Klikněte pravým tlačítkem na **odkazy** uzlu v projektu, který způsobil chybu a zvolte **přidat odkaz**  
  
6.  Klikněte na tlačítko **Windows** kartu a potom **rozšíření** dílčí kartu a potom zrušte zaškrtnutí políček pro staré SDK rozšíření a zaškrtněte políčka pro nové SDK rozšíření. Klikněte na tlačítko **OK**.  
  
## <a name="adding-a-reference-at-design-time"></a>Přidání odkazu v době návrhu  
 Pokud provedete odkaz na sestavení v projektu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vyhledá sestavení v následujících umístěních:  
  
-   Aktuální adresář projektu. (Můžete vyhledat tato sestavení pomocí **Procházet** tab.)  
  
-   Další adresáře projektu ve stejném řešení. (Můžete vyhledat tato sestavení na **projekty** tab.)  
  
> [!NOTE]
>  Všechny projekty obsahují implicitní odkaz na mscorlib. Projekty Visual Basic obsahují implicitní odkaz na `Microsoft.VisualBasic`.  
>   
>  Všechny projekty v sadě Visual Studio obsahují implicitní odkaz na `System.Core`i v případě `System.Core` se odebere ze seznamu odkazů.  
  
## <a name="references-to-shared-components-at-run-time"></a>Odkazy na sdílené komponenty za běhu  
 V době běhu, musí být komponenty v cestě výstupu projektu nebo v [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC). Pokud projekt obsahuje odkaz na objekt, který se nenachází v jednom z těchto umístění, musíte zkopírovat odkaz na výstupní cestu k projektu při sestavování projektu. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> Vlastnost určuje, zda tato kopie má být provedena. Pokud je hodnota **True**, odkaz je zkopírován do adresáře projektu při sestavování projektu. Pokud je hodnota **False**, odkaz není kopírován.  
  
 Pokud nasadíte aplikaci, která obsahuje odkaz na vlastní komponentu registrovanou v mezipaměti GAC, komponenta nebude nasazena s aplikací bez ohledu na to <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> nastavení. V dřívějších verzích [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], můžete nastavit <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> vlastnost v odkazu k zajištění toho, že bylo sestavení nasazeno. Nyní je třeba ručně přidat sestavení do složky \Bin. To umístí všechny vlastní kódy pod kontrolu, což zmenší riziko publikování vlastního kódu, se kterým nejste obeznámeni.  
  
 Ve výchozím nastavení <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> je nastavena na **False** Pokud sestavení nebo komponenta v globální mezipaměti sestavení, nebo je komponentou architektury. V opačném případě je hodnota nastavena na **True**. Odkazy typu projekt projekt jsou vždy nastaveny na **True**.  
  
## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odkazování na projekt nebo sestavení, které cílí na jinou verzi rozhraní .NET Framework  
 Můžete vytvářet aplikace, které odkazují na projekty nebo sestavení, která je jiná cílová verze rozhraní .NET Framework. Například můžete vytvořit aplikaci, který cílí [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] , která odkazuje na sestavení, které cílí na [!INCLUDE[dnprdnext](../includes/dnprdnext-md.md)]. Pokud vytvoříte projekt, který se zaměřuje na starší verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], nemůžete nastavit odkaz v daném projektu na projekt nebo sestavení, který cílí [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] nebo rozhraní .NET Framework verze 4.  
  
 Další informace najdete v tématu [cílení na konkrétní verzi rozhraní .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="project-to-project-references"></a>Odkazy typu projekt projekt  
 Odkazy typu projekt projekt jsou odkazy na projekty obsahující sestavení; Vytvoření s použitím **projektu** kartu. Sada Visual Studio můžete najít sestavení při zadané cestě do projektu.  
  
 Pokud máte projekt, který vytváří sestavení, by měla odkazovat na projekt a nepoužívat odkaz na soubor (viz níže). Výhodou odkazu typu projekt projekt je, že vytvoří závislost mezi projekty v systému sestavení. Závislý projekt bude vytvořen, pokud se změnil od posledního odkazujícího projektu. Odkaz na soubor nevytváří závislost sestavení, takže je možné sestavit odkazující projekt bez vytváření závislého projektu a odkaz se může stát zastaralým. (To znamená, že projekt může odkazovat na dřívější sestavené verze projektu.) Výsledkem může být několik verzí jednoho souboru knihovny DLL požadovaným v adresáři bin, což není možné. Pokud dojde k tomuto konfliktu, zobrazí se zpráva, jako [upozornění: závislost 'file' v projektu 'project' nelze zkopírovat do běhového adresáře, protože by přepsala odkaz 'file'. ](../misc/warning-the-dependency-file-in-project-project-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-file.md). Další informace najdete v tématu [řešení potíží s nefunkční odkazy](../ide/troubleshooting-broken-references.md) a [postupy: vytváření a odebrání závislostí projektu](../ide/how-to-create-and-remove-project-dependencies.md).  
  
> [!NOTE]
>  Odkaz na soubor místo odkazu typu projekt projekt je vytvořen, pokud cílová verze rozhraní .NET Framework jednoho projektu je verze 4.5 a cílová verze jiného projektu je verze 2, 3, 3.5 nebo 4.0.  
  
## <a name="file-references"></a>Odkazy na soubory  
 Odkazy na soubory jsou přímé odkazy na sestavení mimo kontext projektu sady Visual Studio. Vytvoření s použitím **Procházet** karty **správce odkazů**. Použijte odkaz na soubor, pokud jste právě sestavením nebo komponentou a nemají projekt, který vytvoří jako výstup.  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží s poškozenými odkazy](../ide/troubleshooting-broken-references.md)   
 [Programování se sestaveními](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)   
 [Postupy: Přidání nebo odebrání odkazů pomocí správce odkazů](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)


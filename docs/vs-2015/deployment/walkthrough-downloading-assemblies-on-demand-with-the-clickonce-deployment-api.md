---
title: 'Návod: stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af03329a05501427f6d04d6cddbd637c3311b339
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64804954"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Návod: Stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení jsou všechna sestavení obsažená v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci stažena při prvním spuštění aplikace. Můžete ale mít části aplikace, které jsou používány malou sadou uživatelů. V tomto případě chcete stáhnout sestavení pouze při vytvoření některého z jeho typů. Následující návod ukazuje, jak označit určitá sestavení v aplikaci jako "volitelné" a jak je stáhnout pomocí tříd v <xref:System.Deployment.Application> oboru názvů, když to modul CLR (Common Language Runtime) požaduje.  
  
> [!NOTE]
> Aby bylo možné použít tento postup, aplikace bude muset běžet v úplném vztahu důvěryhodnosti.  
  
## <a name="prerequisites"></a>Předpoklady  
 K dokončení tohoto postupu budete potřebovat jednu z následujících součástí:  
  
- Windows SDK. Windows SDK lze stáhnout z webu Microsoft Download Center.  
  
- Visual Studio  
  
## <a name="creating-the-projects"></a>Vytváření projektů  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Vytvoření projektu, který používá sestavení na vyžádání  
  
1. Vytvořte adresář s názvem ClickOnceOnDemand.  
  
2. Otevřete příkazový řádek Windows SDK nebo příkazový [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řádek.  
  
3. Přejděte do adresáře ClickOnceOnDemand.  
  
4. Vygenerujte pár veřejného a privátního klíče pomocí následujícího příkazu:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5. Pomocí poznámkového bloku nebo jiného textového editoru Definujte třídu s názvem `DynamicClass` s jedinou vlastností s názvem `Message` .  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6. Uložte text jako soubor s názvem `ClickOnceLibrary.cs` nebo v `ClickOnceLibrary.vb` závislosti na jazyku, který používáte, do adresáře ClickOnceOnDemand.  
  
7. Zkompilujte soubor do sestavení.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8. Pro získání tokenu veřejného klíče pro sestavení použijte následující příkaz:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Pomocí textového editoru vytvořte nový soubor a zadejte následující kód. Tento kód vytvoří model Windows Forms aplikaci, která stáhne sestavení ClickOnceLibrary v případě potřeby.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. V kódu vyhledejte volání <xref:System.Reflection.Assembly.LoadFile%2A> .  
  
11. Nastavte `PublicKeyToken` na hodnotu, kterou jste načetli dříve.  
  
12. Uložte soubor buď `Form1.cs` nebo `Form1.vb` .  
  
13. Zkompilujte ho do spustitelného souboru pomocí následujícího příkazu.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Označení sestavení jako volitelné  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Chcete-li v aplikaci ClickOnce označit sestavení jako volitelné, použijte MageUI.exe  
  
1. Pomocí MageUI.exe vytvořte manifest aplikace, jak je popsáno v [návodu: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Pro manifest aplikace použijte následující nastavení:  
  
    - Pojmenujte manifest aplikace `ClickOnceOnDemand` .  
  
    - Na stránce **soubory** v řádku ClickOnceLibrary.dll nastavte sloupec **typ souboru** na **None (žádné**).  
  
    - Na stránce **soubory** zadejte do řádku ClickOnceLibrary.dll `ClickOnceLibrary.dll` sloupec **Group (skupina** ).  
  
2. Pomocí MageUI.exe vytvořte manifest nasazení, jak je popsáno v [návodu: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Pro manifest nasazení použijte následující nastavení:  
  
    - Pojmenujte manifest nasazení `ClickOnceOnDemand` .  
  
## <a name="testing-the-new-assembly"></a>Testování nového sestavení  
  
#### <a name="to-test-your-on-demand-assembly"></a>Testování sestavení na vyžádání  
  
1. Nahrajte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení na webový server.  
  
2. Spusťte aplikaci nasazenou pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] z webového prohlížeče zadáním adresy URL manifestu nasazení. Pokud voláte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci `ClickOnceOnDemand` a nahrajete ji do kořenového adresáře adatum.com, vaše adresa URL by vypadala takto:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3. Po zobrazení hlavního formuláře stiskněte klávesu <xref:System.Windows.Forms.Button> . V okně se zprávou by se měl zobrazit řetězec, který čte text "Hello, World!".  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Deployment.Application.ApplicationDeployment>

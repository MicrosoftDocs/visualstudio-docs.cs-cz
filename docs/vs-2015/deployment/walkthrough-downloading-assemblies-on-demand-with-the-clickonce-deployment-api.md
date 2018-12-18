---
title: 'Návod: Stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 6e1f9e1a2115e61e46e0050c1e6504e73c0180fe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199131"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Návod: Stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení, všechna sestavení součástí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace se stáhne při prvním spuštění aplikace. Může však mít částí aplikace, které jsou používány malého počtu uživatelů. V takovém případě budete chtít stáhnout sestavení pouze v případě, že můžete vytvořit jeden z jeho typy. Následující návod ukazuje, jak označit určité sestavení v aplikaci jako "volitelné", a jak si je stáhnout pomocí tříd v <xref:System.Deployment.Application> obor názvů, když je modul CLR (CLR) požaduje.  
  
> [!NOTE]
>  Vaše aplikace bude mít ke spuštění v režimu plné důvěryhodnosti k použití tohoto postupu.  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat jednu z následujících komponent k dokončení tohoto návodu:  
  
-   Windows SDK. Sada Windows SDK můžete stáhnout z webu Microsoft Download Center.  
  
-   Visual Studio.  
  
## <a name="creating-the-projects"></a>Vytváření projektů  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Chcete-li vytvořit projekt, který používá sestavení na vyžádání  
  
1.  Vytvořte adresář ClickOnceOnDemand.  
  
2.  Otevřete příkazový řádek Windows SDK nebo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkazového řádku.  
  
3.  Přejděte do adresáře, ClickOnceOnDemand.  
  
4.  Vygenerujte pár veřejného a privátního klíče pomocí následujícího příkazu:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Pomocí poznámkového bloku nebo jiného textového editoru, definujte třídu s názvem `DynamicClass` s jedinou vlastnost s názvem `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6.  Uložte text jako soubor s názvem `ClickOnceLibrary.cs` nebo `ClickOnceLibrary.vb`, v závislosti na jazyk používáte, k adresáři ClickOnceOnDemand.  
  
7.  Kompilaci do sestavení.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  K získání tokenu veřejného klíče pro sestavení, použijte následující příkaz:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Vytvořte nový soubor pomocí textového editoru a zadejte následující kód. Tento kód vytvoří aplikaci Windows Forms, který stahuje ClickOnceLibrary sestavení, pokud je to požadováno.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. V kódu vyhledejte volání <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Nastavte`PublicKeyToken` hodnotu, která jste získali dříve.  
  
12. Uložte soubor jako buď `Form1.cs` nebo `Form1.vb`.  
  
13. Proveďte jeho kompilaci do spustitelného souboru pomocí následujícího příkazu.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Označení sestavení jako volitelný  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>S použitím MageUI.exe označit sestavení jako volitelný v aplikaci ClickOnce  
  
1.  Vytvořte manifest aplikace pomocí MageUI.exe, jak je popsáno v [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Pro manifest aplikace použijte následující nastavení:  
  
    -   Název manifestu aplikace `ClickOnceOnDemand`.  
  
    -   Na **soubory** stránky, v řádku ClickOnceLibrary.dll nastavit **typ souboru** sloupec **žádný**.  
  
    -   Na **soubory** stránky, v řádku ClickOnceLibrary.dll typ `ClickOnceLibrary.dll` v **skupiny** sloupce.  
  
2.  Pomocí MageUI.exe, vytvořte manifest nasazení, jak je popsáno v [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Pro manifest nasazení použijte následující nastavení:  
  
    -   Název manifestu nasazení `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Testování nového sestavení  
  
#### <a name="to-test-your-on-demand-assembly"></a>K otestování vašeho sestavení na vyžádání  
  
1.  Nahrajte vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení na webový server.  
  
2.  Spusťte aplikaci nasazenou pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] z webového prohlížeče zadáním adresy URL do manifestu nasazení. Při volání vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace `ClickOnceOnDemand`a nahrajte ho do kořenového adresáře adatum.com, adresa URL bude vypadat takto:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Jakmile se zobrazí váš hlavní formulář, stiskněte <xref:System.Windows.Forms.Button>. Měli byste vidět řetězec v okně zprávy pole, která čte "Hello, World!".  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Deployment.Application.ApplicationDeployment>




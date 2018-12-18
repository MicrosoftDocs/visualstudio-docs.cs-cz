---
title: 'Návod: Stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6338044dff5aa5b0555b15b689c04ddd406c50f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887654"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Návod: Stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce
Ve výchozím nastavení, všechna sestavení součástí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace se stáhne při prvním spuštění aplikace. Může však mít částí aplikace, které jsou používány malého počtu uživatelů. V takovém případě budete chtít stáhnout sestavení pouze v případě, že můžete vytvořit jeden z jeho typy. Následující návod ukazuje, jak označit určité sestavení v aplikaci jako "volitelné", a jak si je stáhnout pomocí tříd v <xref:System.Deployment.Application> obor názvů, když je modul CLR (CLR) požaduje.  
  
> [!NOTE]
>  Vaše aplikace bude mít ke spuštění v režimu plné důvěryhodnosti k použití tohoto postupu.  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat jednu z následujících komponent k dokončení tohoto návodu:  
  
-   Windows SDK. Sada Windows SDK můžete stáhnout z webu Microsoft Download Center.  
  
-   Visual Studio.  
  
## <a name="create-the-projects"></a>Vytváření projektů  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Chcete-li vytvořit projekt, který používá sestavení na vyžádání  
  
1. Vytvořte adresář ClickOnceOnDemand.  
  
2. Otevřete příkazový řádek Windows SDK nebo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazového řádku.  
  
3. Přejděte do adresáře, ClickOnceOnDemand.  
  
4. Vygenerujte pár veřejného a privátního klíče pomocí následujícího příkazu:  
  
   ```cmd  
   sn -k TestKey.snk  
   ```  
  
5. Pomocí poznámkového bloku nebo jiného textového editoru, definujte třídu s názvem `DynamicClass` s jedinou vlastnost s názvem `Message`.  
  
    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6. Uložte text jako soubor s názvem *ClickOnceLibrary.cs* nebo *ClickOnceLibrary.vb*, v závislosti na jazyku, se používá *ClickOnceOnDemand* adresáře.  
  
7. Kompilaci do sestavení.  
  
   ```csharp  
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
   ```  
  
   ```vb  
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
   ```  
  
8. K získání tokenu veřejného klíče pro sestavení, použijte následující příkaz:  
  
   ```cmd  
   sn -T ClickOnceLibrary.dll  
   ```  
  
9. Vytvořte nový soubor pomocí textového editoru a zadejte následující kód. Tento kód vytvoří aplikaci Windows Forms, který stahuje ClickOnceLibrary sestavení, pokud je to požadováno.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. V kódu vyhledejte volání <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Nastavte`PublicKeyToken` hodnotu, která jste získali dříve.  
  
12. Uložte soubor jako buď *Form1.cs* nebo *Form1.vb*.  
  
13. Proveďte jeho kompilaci do spustitelného souboru pomocí následujícího příkazu.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="mark-assemblies-as-optional"></a>Označit sestavení jako volitelný  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>S použitím MageUI.exe označit sestavení jako volitelný v aplikaci ClickOnce  
  
1.  Pomocí *MageUI.exe*, vytvořte manifest aplikace, jak je popsáno v [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Pro manifest aplikace použijte následující nastavení:  
  
    -   Název manifestu aplikace `ClickOnceOnDemand`.  
  
    -   Na **soubory** stránku, *ClickOnceLibrary.dll* řádek, nastavte **typ souboru** sloupec, který se **žádný**.  
  
    -   Na **soubory** stránku, *ClickOnceLibrary.dll* řádek, zadejte `ClickOnceLibrary.dll` v **skupiny** sloupce.  
  
2.  Pomocí *MageUI.exe*, vytvořte podle popisu v manifestu nasazení [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Pro manifest nasazení použijte následující nastavení:  
  
    -   Název manifestu nasazení `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Testování nového sestavení  
  
#### <a name="to-test-your-on-demand-assembly"></a>K otestování vašeho sestavení na vyžádání  
  
1. Nahrajte vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení na webový server.  
  
2. Spusťte aplikaci nasazenou pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] z webového prohlížeče zadáním adresy URL do manifestu nasazení. Při volání vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace `ClickOnceOnDemand`a nahrajte ho do kořenového adresáře adatum.com, adresa URL bude vypadat takto:  
  
   ```  
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
   ```  
  
3. Jakmile se zobrazí váš hlavní formulář, stiskněte <xref:System.Windows.Forms.Button>. Měli byste vidět řetězec v okně zprávy pole, která čte "Hello, World!".  
  
## <a name="see-also"></a>Viz také:  
 <xref:System.Deployment.Application.ApplicationDeployment>
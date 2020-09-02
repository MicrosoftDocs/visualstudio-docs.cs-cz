---
title: 'Návod: stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře | Microsoft Docs'
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
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a7ff4fe24720f707c8f3faa330f71a8abda3c698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686339"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Návod: Stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí Návrháře
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení jsou všechna sestavení zahrnutá v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci stažena při prvním spuštění aplikace. Mohou však existovat části aplikace, které jsou používány malou sadou uživatelů. V tomto případě chcete stáhnout sestavení pouze při vytvoření některého z jeho typů. Následující návod ukazuje, jak označit určitá sestavení v aplikaci jako "volitelné" a jak je stáhnout pomocí tříd v <xref:System.Deployment.Application> oboru názvů, pokud je aplikace Common Language Runtime vyžaduje.  
  
> [!NOTE]
> Aby bylo možné použít tento postup, aplikace bude muset běžet v úplném vztahu důvěryhodnosti.  
  
> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, klikněte na položku **Nastavení importu a exportu** v nabídce **nástroje** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-projects"></a>Vytváření projektů  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Vytvoření projektu, který používá sestavení na vyžádání se sadou Visual Studio  
  
1. Vytvořte nový projekt model Windows Forms v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . V nabídce **soubor** přejděte na příkaz **Přidat**a poté klikněte na možnost **Nový projekt**. V dialogovém okně vyberte projekt **knihovny tříd** a pojmenujte jej `ClickOnceLibrary` .  
  
    > [!NOTE]
    > V Visual Basic doporučujeme změnit vlastnosti projektu a změnit tak kořenový obor názvů pro tento projekt na `Microsoft.Samples.ClickOnceOnDemand` nebo na obor názvů podle vašeho výběru. Pro jednoduchost jsou tyto dva projekty v tomto návodu ve stejném oboru názvů.  
  
2. Definujte třídu s názvem `DynamicClass` s jedinou vlastností s názvem `Message` .  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
3. Vyberte projekt model Windows Forms v **Průzkumník řešení**. Přidejte odkaz na <xref:System.Deployment.Application> sestavení a odkaz na projekt do `ClickOnceLibrary` projektu.  
  
    > [!NOTE]
    > V Visual Basic doporučujeme změnit vlastnosti projektu a změnit tak kořenový obor názvů pro tento projekt na `Microsoft.Samples.ClickOnceOnDemand` nebo na obor názvů podle vašeho výběru. Pro jednoduchost se tyto dva projekty v tomto návodu nacházejí ve stejném oboru názvů.  
  
4. Klikněte pravým tlačítkem myši na formulář, klikněte na **Zobrazit kód** v nabídce a do formuláře přidejte následující odkazy.  
  
     [!code-csharp[ClickOnceOnDemand#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemand#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#1)]  
  
5. Přidejte následující kód pro stažení tohoto sestavení na vyžádání. Tento kód ukazuje, jak namapovat sadu sestavení na název skupiny pomocí obecné <xref:System.Collections.DictionaryBase.Dictionary%2A> třídy. Protože v tomto návodu stahujeme jenom jedno sestavení, v naší skupině je jenom jedno sestavení. V reálné aplikaci byste pravděpodobně chtěli stáhnout všechna sestavení související s jednou funkcí v aplikaci současně. Tabulka mapování vám umožní snadnou to provést přidružením všech knihoven DLL, které patří do funkce s názvem skupiny pro stahování.  
  
     [!code-csharp[ClickOnceOnDemand#2](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#2)]
     [!code-vb[ClickOnceOnDemand#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#2)]  
  
6. V nabídce **zobrazení** klikněte na příkaz **Sada nástrojů**. Přetáhněte <xref:System.Windows.Forms.Button> z **panelu nástrojů** do formuláře. Dvakrát klikněte na tlačítko a přidejte následující kód do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.  
  
     [!code-csharp[ClickOnceOnDemand#3](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#3)]
     [!code-vb[ClickOnceOnDemand#3](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#3)]  
  
## <a name="marking-assemblies-as-optional"></a>Označení sestavení jako volitelné  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Označení sestavení jako volitelné ve vaší aplikaci ClickOnce pomocí sady Visual Studio  
  
1. Klikněte pravým tlačítkem na projekt model Windows Forms v **Průzkumník řešení** a klikněte na **vlastnosti**. Vyberte kartu **publikovat** .  
  
2. Klikněte na tlačítko **soubory aplikace** .  
  
3. Vyhledejte výpis pro ClickOnceLibrary.dll. Nastavte rozevírací seznam pro **stav publikování** , který chcete **Zahrnout**.  
  
4. Rozbalte rozevírací seznam **Skupina** a vyberte **Nový**. Jako název zadejte název `ClickOnceLibrary` nové skupiny.  
  
5. Pokračujte v publikování aplikace, jak je popsáno v tématu [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Označení sestavení jako volitelné ve vaší aplikaci ClickOnce pomocí Manifest Generation and Editing Tool – grafický klient (MageUI.exe)  
  
1. Vytvořte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty, jak je popsáno v [návodu: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2. Před zavřením MageUI.exe vyberte kartu, která obsahuje manifest aplikace nasazení a v rámci této karty vyberte kartu **soubory** .  
  
3. Vyhledejte ClickOnceLibrary.dll v seznamu souborů aplikace a nastavte jeho sloupec **typ souboru** na **žádný**. Do sloupce **Skupina** zadejte `ClickOnceLibrary.dll` .  
  
## <a name="testing-the-new-assembly"></a>Testování nového sestavení  
  
#### <a name="to-test-your-on-demand-assembly"></a>Testování sestavení na vyžádání  
  
1. Spusťte aplikaci nasazenou pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
2. Po zobrazení hlavního formuláře stiskněte klávesu <xref:System.Windows.Forms.Button> . V okně se zprávou by se měl zobrazit řetězec, který čte text "Hello, World!".  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Deployment.Application.ApplicationDeployment>

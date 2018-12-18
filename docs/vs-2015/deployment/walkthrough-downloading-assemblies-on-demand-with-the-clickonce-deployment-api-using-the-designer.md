---
title: 'Návod: Stahování sestavení na vyžádání pomocí nasazení ClickOnce pomocí návrháře rozhraní API | Dokumentace Microsoftu'
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
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 923951196487c9dc3f08b61879271fc71be373e4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245060"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Návod: Stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí Návrháře
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení, všechna sestavení součástí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace se stáhne při prvním spuštění aplikace. Ale může být součástí vaší aplikace, které jsou používány malého počtu uživatelů. V takovém případě budete chtít stáhnout sestavení pouze v případě, že můžete vytvořit jeden z jeho typy. Následující návod ukazuje, jak označit určité sestavení v aplikaci jako "volitelné", a jak si je stáhnout pomocí tříd v <xref:System.Deployment.Application> obor názvů, když je modul common language runtime požaduje.  
  
> [!NOTE]
>  Vaše aplikace bude mít ke spuštění v režimu plné důvěryhodnosti k použití tohoto postupu.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-projects"></a>Vytváření projektů  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Chcete-li vytvořit projekt, který používá sestavení na vyžádání pomocí sady Visual Studio  
  
1.  Vytvoření nového projektu Windows Forms v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Na **souboru** nabídky, přejděte k **přidat**a potom klikněte na tlačítko **nový projekt**. Zvolte **knihovny tříd** projektu v dialogovém okně a pojmenujte ho `ClickOnceLibrary`.  
  
    > [!NOTE]
    >  V jazyce Visual Basic, doporučujeme vám, že upravíte vlastnosti projektu, chcete-li změnit kořenový obor názvů pro tento projekt do `Microsoft.Samples.ClickOnceOnDemand` nebo do oboru názvů podle vašeho výběru. Pro jednoduchost jsou tyto dva projekty v tomto názorném postupu ve stejném oboru názvů.  
  
2.  Definovat třídu s názvem `DynamicClass` s jedinou vlastnost s názvem `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
3.  Vyberte projekt Windows Forms v **Průzkumníka řešení**. Přidejte odkaz na <xref:System.Deployment.Application> sestavení a projektu odkaz `ClickOnceLibrary` projektu.  
  
    > [!NOTE]
    >  V jazyce Visual Basic, doporučujeme vám, že upravíte vlastnosti projektu, chcete-li změnit kořenový obor názvů pro tento projekt do `Microsoft.Samples.ClickOnceOnDemand` nebo do oboru názvů podle vašeho výběru. Pro jednoduchost jsou tyto dva projekty v tomto názorném postupu umístěny v stejný obor názvů.  
  
4.  Klikněte pravým tlačítkem na formuláři, klikněte na tlačítko **zobrazit kód** z nabídky a přidejte následující odkazy na formuláři.  
  
     [!code-csharp[ClickOnceOnDemand#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemand#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#1)]  
  
5.  Přidejte následující kód ke stažení tohoto sestavení na vyžádání. Tento kód ukazuje, jak namapovat na název skupiny pomocí obecného sadu sestavení <xref:System.Collections.DictionaryBase.Dictionary%2A> třídy. Vzhledem k tomu, že stahujete pouze jedno sestavení v tomto názorném průvodci, je pouze jedno sestavení v naší skupiny. V reálné aplikaci by pravděpodobně chtít stahovat všechna sestavení, které souvisí s jedinou funkcí v aplikaci ve stejnou dobu. Tabulky mapování umožňuje snadno to provést tím, že přidružíte všechny knihovny DLL, které patří k funkci s názvem skupiny ke stažení.  
  
     [!code-csharp[ClickOnceOnDemand#2](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#2)]
     [!code-vb[ClickOnceOnDemand#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#2)]  
  
6.  Na **zobrazení** nabídky, klikněte na tlačítko **nástrojů**. Přetáhněte <xref:System.Windows.Forms.Button> z **nástrojů** do formuláře. Dvakrát klikněte na tlačítko a přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.  
  
     [!code-csharp[ClickOnceOnDemand#3](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#3)]
     [!code-vb[ClickOnceOnDemand#3](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#3)]  
  
## <a name="marking-assemblies-as-optional"></a>Označení sestavení jako volitelný  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Označit sestavení jako volitelný v aplikaci ClickOnce pomocí sady Visual Studio  
  
1.  Klikněte pravým tlačítkem na projekt Windows Forms v **Průzkumníka řešení** a klikněte na tlačítko **vlastnosti**. Vyberte **publikovat** kartu.  
  
2.  Klikněte na tlačítko **soubory aplikace** tlačítko.  
  
3.  Vyhledejte výpis pro ClickOnceLibrary.dll. Nastavte **stav publikování** rozevíracího seznamu na **zahrnout**.  
  
4.  Rozbalte **skupiny** rozevíracího seznamu a vyberte **nový**. Zadejte název `ClickOnceLibrary` jako název nové skupiny.  
  
5.  Pokračovat v publikování vaší aplikace, jak je popsáno v [postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Označit sestavení jako volitelný v aplikaci ClickOnce pomocí Manifest Generation and Editing Tool, grafický klient (MageUI.exe)  
  
1.  Vytvoření vašeho [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty, jak je popsáno v [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Před zavřením MageUI.exe, vyberte kartu, která obsahuje manifest aplikace tohoto nasazení a v rámci této karty vyberte **soubory** kartu.  
  
3.  Vyhledání ClickOnceLibrary.dll v seznamu souborů aplikace a nastavení jeho **typ souboru** sloupec **žádný**. Pro **skupiny** sloupců, typ `ClickOnceLibrary.dll`.  
  
## <a name="testing-the-new-assembly"></a>Testování nového sestavení  
  
#### <a name="to-test-your-on-demand-assembly"></a>K otestování vašeho sestavení na vyžádání  
  
1.  Spusťte aplikaci nasazenou pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
2.  Jakmile se zobrazí váš hlavní formulář, stiskněte <xref:System.Windows.Forms.Button>. Měli byste vidět řetězec v okně zprávy pole, která čte "Hello, World!"  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Deployment.Application.ApplicationDeployment>




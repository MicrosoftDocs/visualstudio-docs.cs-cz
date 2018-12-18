---
title: 'Postupy: vystavení kódu do VBA ve Vizuálu C# projektu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f00f668c3eac9a39251d0a4e19f98ed597c373db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873484"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Postupy: vystavení kódu do VBA ve Vizuálu C# projektu
  Kód ve Vizuálu můžete zveřejnit C# projektu jazyka Visual Basic pro kód Applications (VBA) Pokud chcete, aby dva typy kódu komunikovat mezi sebou.  
  
 Vizuál C# proces se liší od procesu jazyka Visual Basic. Další informace najdete v tématu [postupy: vystavení kódu do VBA v projektu jazyka Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="expose-code-in-a-visual-c-project"></a>Vystavení kódu ve Vizuálu C# projektu  
 Povolit kód VBA pro volání kódu ve Vizuálu C# projektu a upravte kód tak, aby byl viditelný modulům COM, nastavte **ReferenceAssemblyFromVbaProject** vlastnost **True** v návrháři.  
  
 Návod, který ukazuje, jak volat metodu ve Vizuálu C# projektu z jazyka VBA, naleznete v tématu [návod: volání kódu z jazyka VBA v aplikaci Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Vystavení kódu ve Vizuálu C# projektu pro jazyk VBA  
  
1. Otevřete nebo vytvořte projekt úrovni dokumentu, který je založen na dokument aplikace Word, Excelový sešit nebo šablonu v Excelu, který podporuje makra a kód VBA, který již obsahuje.  
  
    Další informace o formátech soubor dokumentu, které podporují makra najdete v tématu [kombinovat VBA a přizpůsobení na úrovni dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
   > [!NOTE]  
   >  Tuto funkci nelze použít v projektech aplikace Word šablony.  
  
2. Ujistěte se, že kód VBA v dokumentu může spustit bez výzvy pro uživatele povolit makra. VBA kód ke spuštění tak, že přidáte do seznamu důvěryhodných umístění v nastavení Centra zabezpečení pro aplikaci Word nebo Excel umístění projektu Office, kterému můžete důvěřovat.  
  
3. Přidat člena, který chcete zpřístupnit pro jazyk VBA veřejnou třídu ve vašem projektu a deklarace nového člena jako **veřejné**.  
  
4. Použijte následující <xref:System.Runtime.InteropServices.ComVisibleAttribute> a <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributy do třídy, které jsou vystaveny pro jazyk VBA. Tyto atributy zviditelnit třídy modelu COM, ale bez generování třídy rozhraní.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   [System.Runtime.InteropServices.ClassInterface(  
       System.Runtime.InteropServices.ClassInterfaceType.None)]  
   ```  
  
5. Přepsat **GetAutomationObject** metoda třídy položku hostitele ve vašem projektu a vrátit instanci třídy, které jsou vystaveny pro jazyk VBA:  
  
   - Pokud jsou vystaveny položky třída hostitele pro jazyk VBA, má přednost před **GetAutomationObject** metodu, která patří do této třídy a vracet aktuální instance třídy.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return this;  
     }  
     ```  
  
   - Pokud jsou vystaveny třídu, která není položka hostitele pro jazyk VBA, má přednost před **GetAutomationObject** metoda libovolného hostitele položky ve vašem projektu a vrátit instanci třídy jiné než hostitelské položky. Například následující kód předpokládá, že jsou vystaveny třídu s názvem `DocumentUtilities` pro jazyk VBA.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return new DocumentUtilities();  
     }  
     ```  
  
     Další informace o hostitelských položkách naleznete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
6. Extrahujte rozhraní ze třídy, které jsou vystaveny pro jazyk VBA. V **extrahování rozhraní** dialogovém okně vyberte veřejné členy, které chcete zahrnout v deklaraci rozhraní. Další informace najdete v tématu [extrahovat rozhraní refaktoring](../ide/reference/extract-interface.md).
  
7. Přidat **veřejné** – klíčové slovo k deklaraci rozhraní.  
  
8. Zkontrolujte viditelné modelu COM rozhraní přidáním následujícího kódu <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut rozhraní.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   ```  
  
9. Otevřete v Návrháři v dokumentu (pro aplikaci Word) nebo listu (Excel) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. V **vlastnosti** okna, vyberte **ReferenceAssemblyFromVbaProject** vlastnost a změňte hodnotu na **True**.  
  
    > [!NOTE]  
    >  Pokud sešit nebo dokument už neobsahuje kód VBA, nebo pokud kód VBA v dokumentu není důvěryhodný pro spuštění, zobrazí se chybová zpráva při nastavení **ReferenceAssemblyFromVbaProject** vlastnost **True**. Je to proto, že Visual Studio nelze upravit projektu VBA v dokumentu v této situaci.  
  
11. Klikněte na tlačítko **OK** ve zprávě, která se zobrazí. Tato zpráva upozorní, že pokud přidáte VBA kód v sešitu nebo při spuštění projektu z dokumentu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], kód VBA budou ztraceny při příštím sestavení projektu. Je to proto, že dokument v buildu výstupní složky je přepsána pokaždé, když vytváříte projekt.  
  
     V tomto okamžiku sady Visual Studio nastaví projekt tak, aby projekt VBA může volat do sestavení. Visual Studio také přidá metodu s názvem `GetManagedClass` do projektu VBA. Tuto metodu lze volat z libovolného místa v projektu VBA pro přístup ke třídě, která je vystavena VBA.  
  
12. Sestavte projekt.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Kombinování přizpůsobení na úrovni dokumentu a VBA](../vsto/combining-vba-and-document-level-customizations.md)   
 [Návod: Volání kódu z jazyka VBA v aplikaci Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Postupy: vystavení kódu do VBA v projektu jazyka Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  
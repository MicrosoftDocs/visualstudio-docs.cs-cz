---
title: Pokyny pro vytváření oblastí formulářů aplikace Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 535ab0329412b261b06fb2d04daefe817299dbe9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892009"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Pokyny pro vytváření oblastí formulářů aplikace Outlook
  Můžou pomoct následující informace, optimalizace vaší oblasti formuláře a vyhnout se potenciální problémy:  
  
- [Použít názvy oblastí formuláře](#UsingFormRegions).  
  
- [Zakázat dědičnost oblasti formulářů](#DisablingInheritance).  
  
- [Principy typů a názvy tříd zpráv](#ClassNames).  
  
- [Návrh přiléhající k oblasti formuláře pro podokno čtení](#ReadingPane).  
  
- [Použijte ikonu optimální velikosti](#UsingOptimal).  
  
  Další informace o oblasti formuláře, naleznete v tématu [oblastí formulářů aplikace Outlook vytvořit](../vsto/creating-outlook-form-regions.md).  
  
  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a> Použít názvy oblastí formuláře  
 Existuje několik názvů používaných k popisu oblasti formuláře. Je důležité porozumět rozdílu mezi těmito názvy a jaký vliv mají oblasti formuláře. Následující tabulka popisuje každý název.  
  
|Název oblasti formuláře|Popis|  
|----------------------|-----------------|  
|Název položky oblasti formuláře|Název, který zadáte pro **oblast formuláře Outlooku** položky v **přidat novou položku** dialogové okno. Toto je název souboru kódu oblasti formuláře, který se zobrazí v **Průzkumníka řešení**.|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> Vlastnost|Zadejte tento název **zadání popisného textu a výběr předvoleb zobrazení** stránku **novou oblast formuláře Outlooku** průvodce. Tento název se zobrazí jako **FormRegionName** vlastnost **vlastnosti** okna.<br /><br /> Použití <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> vlastnosti a určit tak popisek, který identifikuje oblasti formuláře v uživatelském rozhraní (UI) aplikace Outlook. Tento název se zobrazí jako tlačítko na pásu karet položky Outlooku pro oblasti samostatné formuláře.<br /><br /> Tento název se zobrazí jako text záhlaví nad oblasti formuláře pro sousední oblasti formuláře.|  
|`Microsoft.Office.Tools.Outlook.FormRegionName` Atribut|Když přidáte **oblast formuláře Outlooku** položky do projektu, Visual Studio nastaví tuto vlastnost na plně kvalifikovaný název oblasti formuláře. Výchozí plně kvalifikovaný název je název doplňku VSTO připojeným k názvu oblasti formuláře tečkou, třeba `OutlookAddIn1.FormRegion1`.<br /><br /> Tento plně kvalifikovaný název se zobrazí také jako atribut v horní části třídy objekt pro vytváření oblasti formuláře.<br /><br /> Použití `Microsoft.Office.Tools.Outlook.FormRegionName` atribut jednoznačně identifikuje oblasti formuláře na všech doplňků VSTO pro Outlook. Nelze změnit hodnotu `Microsoft.Office.Tools.Outlook.FormRegionName` atribut přejmenování položky oblasti formuláře nebo změnou <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> vlastnost. Chcete-li změnit tento název, je třeba upravit `Microsoft.Office.Tools.Outlook.FormRegionName` atributu v souboru kódu oblasti formuláře.|  
  
##  <a name="DisablingInheritance"></a> Zakázat dědičnost oblasti formuláře  
 Ve výchozím nastavení vlastní třídu zpráv dědí všechna přidružení oblasti formuláře třídy základní zprávy. Například třída zprávy s názvem `IPM.Task.Contoso` je odvozena z `IPM.Task`. Proto `IPM.Task.Contoso` dědí přidružení oblasti formuláře `IPM.Task`.  
  
 Pokud nechcete, aby se oblast formuláře, který se má přidružit žádné odvozené třídy zpráv, nastavte <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> vlastnost oblasti formuláře k **true**. Například, pokud přiřadíte sousední oblasti formuláře s `IPM.Task` a nastavit <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> vlastnost **true**, oblast formuláře bude připojen pouze k dolnímu okraji formuláři standardní úlohy. Oblast formuláře se nepřipojí k dolnímu okraji libovolné upravené verze formuláři standardní úlohy.  
  
##  <a name="ClassNames"></a> Pochopení typů a názvů tříd zpráv  
 Název typu položky aplikace Outlook se liší od názvu třídy zpráv položky aplikace Outlook. Například, že název typu položky RSS je `Microsoft.Office.Interop.Outlook.PostItem`. Název třídy zpráv položky RSS je `IPM.Post.RSS`.  
  
 Odkažte na položku aplikace Outlook v kódu pomocí názvu typu. Seznam názvů typů najdete v tématu [přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
 Použijte název třídy zpráv Outlooku položek v **novou oblast formuláře Outlooku** průvodce k položce přidružení oblasti formuláře. Seznam názvů tříd zpráv najdete v tématu [přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
##  <a name="ReadingPane"></a> Návrh sousední oblasti formuláře pro podokno čtení  
 V podokně čtení Outlook můžete bez otevření položky ve verzi preview položky aplikace Outlook. V podokně čtení je určen jen pro čtení. Proto vstupních ovládacích prvků přidaných na sousední oblasti formuláře, jako je textové pole, nemusí se chovat dle očekávání při položky a formulář oblasti jsou otevřeny v podokně čtení.  
  
 Například pokud položka, která má sousední oblasti formuláře je otevřen v podokně čtení, následující situaci je možné:  
  
1. Vyberte nějaký text do textového pole, která je na oblast formuláře.  
  
2. Stisknutím klávesy **odstranit**.  
  
3. Namísto textu v textovém poli se odstraní položka celou e-mailu.  
  
   Pokud navrhujete sousední oblasti formuláře, který obsahuje vstupní ovládací prvky, otestujte ovládací prvky v podokně čtení a ujistěte se, že správně fungují. Zvažte možnost přidat vlastní kód, který zakáže ovládací prvky, které nejsou chovat dle očekávání.  
  
   Alternativně můžete nastavit <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> vlastnost oblasti formuláře k **False**. Tímto způsobem oblasti formuláře nelze použít v podokně čtení.  
  
##  <a name="UsingOptimal"></a> Použijte ikonu optimální velikosti  
 Můžete určit, které ikony má oblast formuláře zobrazit ikonu nastavením vlastností v **ikony** skupina vlastností **vlastnosti** okna. K dosažení nejlepší vizuální kvality pomocí následujících pokynů:  
  
- Pro **stránky** ikonu, použijte soubor Portable Network Graphics (PNG).  
  
- **Okno** ikony by měl být 32 x 32 pixelů.  
  
- Další ikony musí být 16 x 16 pixelů.  
  
  **Stránky** ikona na pásu karet je kontrola pro položky, které mají samostatné, nahrazení nebo oblastí formulářů nahradit všechno.  
  
  **Okno** ikona v oznamovací oblasti a **Alt**+**kartu** dialogové okno pro otevřené položky tohoto zobrazení nahrazení nebo nahradit všechno formuláře oblasti.  
  
## <a name="see-also"></a>Viz také:  
 [Přístup k oblasti formuláře za běhu](../vsto/accessing-a-form-region-at-run-time.md)   
 [Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)   
 [Návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Postupy: přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  
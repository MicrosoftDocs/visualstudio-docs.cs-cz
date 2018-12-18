---
title: 'Postupy: mapování schémat na dokumenty aplikace Word v sadě Visual Studio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e3bec0437fb9bcd55821e27b22b118430024f751
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255428"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Postupy: mapování schémat na dokumenty aplikace Word v sadě Visual Studio
  **Důležité** informace uvedené v tomto tématu týkající se aplikace Microsoft Word je vidění výhradně pro benefit a použití jednotlivce a organizace, kteří se nacházejí mimo Spojené státy a jeho území nebo který používáte, nebo vývoj programy, které běží na, produkty Microsoft Word, které byly před leden 2010, když Microsoft odebrat implementace konkrétní funkce licencí společnosti Microsoft týkající se vlastní kód XML z aplikace Microsoft Word. Tyto informace týkající se aplikace Microsoft Word nemusí přečteny nebo používány jednotlivce nebo organizace v USA nebo v jeho území, které používáte, nebo vývoj programy, které běží na produkty Microsoft Word, které byly licencí společnosti Microsoft po 10 leden 2010 ; tyto produkty nebudou chovají stejně jako produkty licencované před tímto datem nebo zakoupených a licenci na použití mimo Spojené státy.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Dokument je otevřen v sadě Visual Studio, můžete namapovat schéma XML do dokumentu. Můžete použít stejné nástroje Microsoft Office Word, které použijete v otevřeném dokumentu mimo Visual Studio. Microsoft Office project vytvoří stejné objekty, zda mapování schématu v dokumentu před nebo po vytvoření řešení aplikace Word.  
  
## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Pro mapování schématu XML na dokument aplikace Word v sadě Visual Studio  
  
1.  Otevřete projekt dokumentu nebo šablony aplikace Word v sadě Visual Studio.  
  
2.  Klikněte v dokumentu, který má přesunout fokus na návrháře.  
  
3.  Na pásu karet klikněte na **vývojáře** kartě.  
  
    > [!NOTE]  
    >  Pokud **vývojáře** karta není viditelný, musíte ji nejdříve zobrazit. Další informace najdete v tématu [postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  V **XML** klikněte na možnost **schématu**.  
  
     **Šablony a doplňky** otevře se dialogové okno.  
  
5.  Klikněte **schématu XML** kartě.  
  
6.  Klikněte na tlačítko **přidat schématu**.  
  
     **Přidat schéma** otevře se dialogové okno.  
  
7.  Přejděte do souboru schématu, vyberte ho a pak klikněte na tlačítko **otevřete**.  
  
     **Schéma – nastavení** otevře se dialogové okno.  
  
8.  Přiřadit alias nebo klikněte na tlačítko **OK** přidat schéma bez alias.  
  
9. Click **OK**.  
  
     **Struktuře XML** otevře se okno.  
  
10. Přetáhněte elementy z **struktuře XML** okno na místa v dokumentu, kde chcete vytvořit odpovídající ovládací prvky.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: mapování schémat na listy v sadě Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Schémata XML a data v přizpůsobeních na úrovni dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  
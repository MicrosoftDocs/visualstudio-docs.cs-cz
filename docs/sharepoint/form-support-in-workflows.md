---
title: Podpora formulářů v pracovních postupech | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 27e8ab6651c6838de92b8a3d83311ebd47fabcbb
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296187"
---
# <a name="form-support-in-workflows"></a>Podpora formulářů v pracovních postupech
  Čtyři typy formulářů lze použít v pracovní postup: přidružení, inicializace, úloh a úpravy. Tyto typy formuláře může být založen na formulář ASPX nebo formuláře aplikace InfoPath. Úroveň podpory, který [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] poskytuje pro konkrétní formulář závisí na několika faktorech, které jsou popsány v následujících tabulkách. Další informace o typech formuláře pracovního postupu najdete v tématu [Přehled formuláře pracovního postupu](http://go.microsoft.com/fwlink/?LinkId=185228).  
  
## <a name="xml-refactoring"></a>Refaktoring XML
 Když přidáte ASPX přidružení nebo inicializační formulář k [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] položky projektu pracovního postupu, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automaticky refactors XML v pracovním postupu *Elements.xml* souboru se má zachovat atributu, který odkazuje na přidružení nebo odstranění inicializační formulář synchronizované pokaždé, když se aktualizuje název nebo nasazení cestu formuláře nebo formuláře. Ale při použití jiných typů formuláře v pracovním postupu, jako je například formuláři úkolu nebo úpravy *Elements.xml* souboru není Refaktorovat.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Podpora formulářů v nových pracovních postupů sady Visual Studio
 Následující tabulka uvádí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] podpory pro různé typy ve formulářích ASPX nebo aplikace InfoPath v pracovních postupech, které jsou vytvořeny v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Typ formuláře|Pracovní postup vytvořený v sadě Visual Studio se formulář ASPX|Pracovní postup vytvořený v sadě Visual Studio pomocí formuláře aplikace InfoPath|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Přidružení|-Formulář přidružení ASPX lze přidat do pracovního postupu pomocí **formulář přidružení pracovního postupu** šablony položky.<br />– *Elements.xml* soubor pracovního postupu je teď vyčleněný při přidání, přejmenovat nebo odstranit formuláře nebo při změně jeho cesta nasazení.<br />-Další informace najdete v tématu [návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|– Neexistuje žádná šablona přidružení formuláře aplikace InfoPath v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a aplikace InfoPath Designer.<br />– *Elements.xml* soubor pracovního postupu není Refaktorovat.|  
|Zahájení|Inicializační formulář – ASPX lze přidat do pracovního postupu pomocí **inicializační formulář pracovního postupu** šablony položky.<br />– *Elements.xml* soubor pracovního postupu je teď vyčleněný při přidání, přejmenovat nebo odstranit formuláře nebo při změně jeho cesta nasazení.<br />-Další informace najdete v tématu [návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|– Neexistuje žádná šablona přidružení formuláře aplikace InfoPath v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a aplikace InfoPath Designer.<br />– *Elements.xml* soubor pracovního postupu není Refaktorovat.|  
|Úloha|-Je k dispozici v šabloně žádné úlohy ASPX [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Musíte vytvořit stránku aplikace a přidejte do ní kód.<br />– *Elements.xml* soubor pracovního postupu není Refaktorovat.<br />-Další informace najdete v tématu [formuláře pracovního postupu úloh (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|– Neexistuje žádná šablona úkol formuláře aplikace InfoPath v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a aplikace InfoPath Designer.<br />– *Elements.xml* soubor pracovního postupu není Refaktorovat.|  
|Úpravy|-Je k dispozici v šabloně žádné úpravy ASPX [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Přidat formulář úprav, musíte vytvořit stránku aplikace a přidejte do ní kód.<br />– *Elements.xml* soubor pracovního postupu není Refaktorovat. Musíte je ručně upravit podle potřeby.<br />-Další informace najdete v tématu [formuláře úprav pracovního postupu (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|– Neexistuje žádná šablona změny formuláře InfoPath v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a aplikace InfoPath Designer.<br />– *Elements.xml* soubor pracovního postupu není Refaktorovat.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Podpora formulářů v importované opakovaně použitelných pracovních postupů služby SharePoint
 Následující tabulka uvádí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] podpory pro různé typy ve formulářích ASPX nebo aplikace InfoPath v opakovaně použitelných pracovních postupů služby SharePoint, které jsou importovány do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Typ formuláře|Opakovaně použitelného pracovního postupu, který má formulář ASPX naimportované z Návrháře služby SharePoint|Opakovaně použitelného pracovního postupu, který má formuláře aplikace InfoPath, který je importován z aplikace SharePoint Designer|  
|---------------|-------------------------------------------------------------------------------| - |  
|Přidružení|-Formuláři odkazuje *Elements.xml* soubor pracovního postupu.<br />– *Elements.xml* soubor pracovního postupu je teď vyčleněný při formuláře je přejmenována nebo odstraněna, nebo při změně jeho cesta nasazení.|-Formuláři importováno, ale neodkazuje v *Elements.xml* pracovního postupu.<br />– *Elements.xml* soubor pracovního postupu není Refaktorovat.|  
|Zahájení|-Formuláře se odkazuje pomocí pracovního postupu v *Elements.xml* soubor pracovního postupu.<br />– *Elements.xml* soubor pracovního postupu je teď vyčleněný při formuláře je přejmenována nebo odstraněna, nebo při změně jeho cesta nasazení.|-Formuláři importováno, ale neodkazuje v *Elements.xml* pracovního postupu.<br />– *Elements.xml* soubor pracovního postupu není Refaktorovat. **Poznámka:** pravidla a vlastnosti musí být přidán a změnit pro tento scénář fungovat.|  
|Úloha|-Formuláři odkazuje *Elements.xml* soubor pracovního postupu.<br />– *Elements.xml* soubor pracovního postupu není Refaktorovat.|-Formuláři importováno, ale neodkazuje v *Elements.xml* pracovního postupu.<br />– *Elements.xml* soubor pracovního postupu není Refaktorovat. **Poznámka:** pravidla a vlastnosti musí být přidán a změnit pro tento scénář fungovat.|  
|Úpravy|Nelze použít. Formuláře úprav ASPX nelze vytvořit v SharePoint designeru.|Nelze použít. Úpravy formulářů InfoPath nelze vytvořit v aplikaci SharePoint Designer, s výjimkou integrované serveru SharePoint Server pracovního postupu, která není zahrnutá v souboru WSP při exportu pracovního postupu.|  
  
## <a name="see-also"></a>Viz také:
 [Návod: Vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Vytváření řešení pracovního postupu služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Import položek z existující stránky SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  

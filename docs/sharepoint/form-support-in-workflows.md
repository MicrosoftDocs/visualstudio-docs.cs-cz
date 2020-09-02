---
title: Podpora formulářů v pracovních postupech | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b064df6729b914af7758cde86b03b886fd0e5d26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986265"
---
# <a name="form-support-in-workflows"></a>Podpora formulářů v pracovních postupech
  V pracovním postupu lze použít čtyři typy formulářů: přidružení, zahájení, úloha a změna. Tyto typy formulářů můžou být založené buď na formuláři ASPX, nebo ve formuláři InfoPath. Úroveň podpory, která [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] poskytuje konkrétní formulář, závisí na několika faktorech, které jsou popsány v následujících tabulkách. Další informace o typech formuláře pracovního postupu najdete v tématu [Přehled formulářů pracovních postupů](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>Refaktoring XML
 Když do položky projektu pracovního postupu přidáte přidružení ASPX nebo inicializační formulář [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , automaticky se [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] refaktoruje kód XML v souboru *Elements.xml* pracovního postupu, aby zůstal atribut, který odkazuje na přidružení nebo spouštěcí formulář, v synchronizaci pokaždé, když se aktualizuje název formuláře nebo cesta nasazení, nebo dojde k odstranění formuláře. Pokud však v pracovním postupu použijete jiné typy formulářů, jako je například úkol nebo formulář pro úpravy, soubor *Elements.xml* není refaktored.

## <a name="form-support-in-new-visual-studio-workflows"></a>Podpora formulářů v nových pracovních postupech sady Visual Studio
 Následující tabulka obsahuje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] podporu různých typů formulářů v rámci formulářů aspx nebo InfoPath v pracovních postupech, které jsou vytvořeny v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Typ formuláře|Pracovní postup vytvořený v aplikaci Visual Studio s formulářem ASPX|Pracovní postup vytvořený v aplikaci Visual Studio pomocí formuláře InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Řídí|– Formulář přidružení ASPX se dá do pracovního postupu přidat pomocí šablony položky **formuláře přidružení pracovního postupu** .<br />– Soubor *Elements.xml* pracovního postupu se refaktoruje při přidání, přejmenování nebo odstranění formuláře nebo při změně jeho cesty nasazení.<br />– Další informace najdete v tématu [Návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-V není žádná šablona formuláře přidružení aplikace InfoPath [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikací a návrhářem aplikace InfoPath.<br />– Soubor *Elements.xml* pracovního postupu není refaktored.|
|Odůvodňují|– Inicializační formulář ASPX lze přidat do pracovního postupu pomocí šablony položky **inicializačního formuláře pracovního postupu** .<br />– Soubor *Elements.xml* pracovního postupu se refaktoruje při přidání, přejmenování nebo odstranění formuláře nebo při změně jeho cesty nasazení.<br />– Další informace najdete v tématu [Návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-V není žádná šablona formuláře přidružení aplikace InfoPath [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikací a návrhářem aplikace InfoPath.<br />– Soubor *Elements.xml* pracovního postupu není refaktored.|
|Úkol|-Žádná šablona formuláře úlohy ASPX není k dispozici v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Je nutné vytvořit stránku aplikace a přidat do ní kód.<br />– Soubor *Elements.xml* pracovního postupu není refaktored.<br />– Další informace najdete v tématu [formuláře úkolů pracovního postupu (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14)) .|-V nástroji není žádná šablona formuláře úlohy InfoPath [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikací a návrhářem aplikace InfoPath.<br />– Soubor *Elements.xml* pracovního postupu není refaktored.|
|Úprava|– Není k dispozici žádná šablona formuláře pro úpravu ASPX v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Chcete-li přidat formulář pro úpravy, je nutné vytvořit stránku aplikace a přidat do ní kód.<br />– Soubor *Elements.xml* pracovního postupu není refaktored. V případě potřeby je nutné ručně upravit.<br />– Další informace najdete v tématu [formuláře pro úpravy pracovního postupu (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14)) .|-V nástroji neexistuje žádná šablona formuláře pro úpravu aplikace InfoPath [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikací a návrhářem aplikace InfoPath.<br />– Soubor *Elements.xml* pracovního postupu není refaktored.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Podpora formulářů v importovaných pracovních postupech služby SharePoint
 Následující tabulka obsahuje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] podporu různých typů formulářů v rámci formulářů aspx nebo InfoPath v opakovaně použitelných pracovních postupech služby SharePoint, které jsou importovány do nástroje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Typ formuláře|Opakovaně použitelný pracovní postup, který má naimportovaný formulář ASPX z návrháře služby SharePoint|Opakovaně použitelný pracovní postup, který obsahuje formulář aplikace InfoPath importovaný z aplikace SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Řídí|– Na formulář se odkazuje v souboru *Elements.xml* pracovního postupu.<br />– Soubor *Elements.xml* pracovního postupu se refaktoruje, když se formulář přejmenuje nebo odstraní nebo když se změní jeho cesta nasazení.|– Formulář se importuje, ale neodkazuje se na *Elements.xml* pracovního postupu.<br />– Soubor *Elements.xml* pracovního postupu není refaktored.|
|Odůvodňují|– Na formulář odkazuje pracovní postup v souboru *Elements.xml* pracovního postupu.<br />– Soubor *Elements.xml* pracovního postupu se refaktoruje, když se formulář přejmenuje nebo odstraní nebo když se změní jeho cesta nasazení.|– Formulář se importuje, ale neodkazuje se na *Elements.xml* pracovního postupu.<br />– Soubor *Elements.xml* pracovního postupu není refaktored. **Poznámka:**  Pro tento scénář je nutné přidat a změnit pravidla a vlastnosti pro fungování.|
|Úkol|– Na formulář se odkazuje v souboru *Elements.xml* pracovního postupu.<br />– Soubor *Elements.xml* pracovního postupu není refaktored.|– Formulář se importuje, ale neodkazuje se na *Elements.xml* pracovního postupu.<br />– Soubor *Elements.xml* pracovního postupu není refaktored. **Poznámka:**  Pro tento scénář je nutné přidat a změnit pravidla a vlastnosti pro fungování.|
|Úprava|Neužívá se. V Návrháři SharePoint nelze vytvořit formuláře změny ASPX.|Neužívá se. Formuláře úprav aplikace InfoPath nelze vytvořit v Návrháři služby SharePoint, s výjimkou integrovaného pracovního postupu serveru SharePoint, který není součástí souboru. wsp při exportu pracovního postupu.|

## <a name="see-also"></a>Viz také
- [Návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Vytváření řešení pracovního postupu služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Import položek z existujícího webu služby SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)

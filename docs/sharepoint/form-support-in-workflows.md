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
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986265"
---
# <a name="form-support-in-workflows"></a>Podpora formulářů v pracovních postupech
  V pracovním postupu lze použít čtyři typy formulářů: přidružení, zahájení, úloha a změna. Tyto typy formulářů můžou být založené buď na formuláři ASPX, nebo ve formuláři InfoPath. Úroveň podpory, kterou [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] poskytuje pro konkrétní formulář, závisí na několika faktorech, které jsou popsány v následujících tabulkách. Další informace o typech formuláře pracovního postupu najdete v tématu [Přehled formulářů pracovních postupů](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>Refaktoring XML
 Když přidáte přidružení ASPX nebo inicializační formulář do položky projektu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pracovního postupu, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automaticky refaktoruje kód XML v souboru *Elements. XML* pracovního postupu, aby zůstal atribut, který odkazuje na přidružení nebo inicializační formulář, synchronizován. pokaždé, když se aktualizuje název formuláře nebo cesta nasazení nebo dojde k odstranění formuláře. Pokud však použijete jiné typy formulářů v pracovním postupu, jako je například formulář úlohy nebo změny, soubor *Elements. XML* není refaktored.

## <a name="form-support-in-new-visual-studio-workflows"></a>Podpora formulářů v nových pracovních postupech sady Visual Studio
 V následující tabulce jsou uvedeny [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] podporu různých typů formulářů v rámci formulářů ASPX nebo InfoPath v pracovních postupech, které jsou vytvořeny v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

|Typ formuláře|Pracovní postup vytvořený v aplikaci Visual Studio s formulářem ASPX|Pracovní postup vytvořený v aplikaci Visual Studio pomocí formuláře InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Řídí|– Formulář přidružení ASPX se dá do pracovního postupu přidat pomocí šablony položky **formuláře přidružení pracovního postupu** .<br />– Soubor *Elements. XML* pracovního postupu se refaktoruje při přidání, přejmenování nebo odstranění formuláře nebo při změně jeho cesty nasazení.<br />– Další informace najdete v tématu [Návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]neexistuje žádná šablona formuláře přidružení aplikace InfoPath.<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a InfoPath designerem.<br />– Soubor *Elements. XML* pracovního postupu není refaktored.|
|Odůvodňují|– Inicializační formulář ASPX lze přidat do pracovního postupu pomocí šablony položky **inicializačního formuláře pracovního postupu** .<br />– Soubor *Elements. XML* pracovního postupu se refaktoruje při přidání, přejmenování nebo odstranění formuláře nebo při změně jeho cesty nasazení.<br />– Další informace najdete v tématu [Návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]neexistuje žádná šablona formuláře přidružení aplikace InfoPath.<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a InfoPath designerem.<br />– Soubor *Elements. XML* pracovního postupu není refaktored.|
|Úloha|-V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]není k dispozici žádná šablona formuláře úlohy ASPX. Je nutné vytvořit stránku aplikace a přidat do ní kód.<br />– Soubor *Elements. XML* pracovního postupu není refaktored.<br />– Další informace najdete v tématu [formuláře úkolů pracovního postupu (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14)) .|-V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]neexistuje žádná šablona formuláře úlohy InfoPath.<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a InfoPath designerem.<br />– Soubor *Elements. XML* pracovního postupu není refaktored.|
|Měně|-V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]není k dispozici žádná šablona formuláře pro úpravu ASPX. Chcete-li přidat formulář pro úpravy, je nutné vytvořit stránku aplikace a přidat do ní kód.<br />– Soubor *Elements. XML* pracovního postupu není refaktored. V případě potřeby je nutné ručně upravit.<br />– Další informace najdete v tématu [formuláře pro úpravy pracovního postupu (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14)) .|-V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]neexistuje žádná šablona formuláře pro úpravu aplikace InfoPath.<br />– Neexistuje žádná integrace mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a InfoPath designerem.<br />– Soubor *Elements. XML* pracovního postupu není refaktored.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Podpora formulářů v importovaných pracovních postupech služby SharePoint
 V následující tabulce jsou uvedeny [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] podporu různých typů formulářů ve formulářích ASPX nebo InfoPathu v opakovaně použitelných pracovních postupech služby SharePoint, které jsou importovány do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

|Typ formuláře|Opakovaně použitelný pracovní postup, který má naimportovaný formulář ASPX z návrháře služby SharePoint|Opakovaně použitelný pracovní postup, který obsahuje formulář aplikace InfoPath importovaný z aplikace SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Řídí|– Formulář je odkazován v souboru *Elements. XML* pracovního postupu.<br />– Soubor *Elements. XML* pracovního postupu se refaktoruje při přejmenování nebo odstranění formuláře nebo při změně jeho cesty nasazení.|– Formulář se importuje, ale neodkazuje se na *elementy. XML* pracovního postupu.<br />– Soubor *Elements. XML* pracovního postupu není refaktored.|
|Odůvodňují|– Na formulář odkazuje pracovní postup v souboru *Elements. XML* pracovního postupu.<br />– Soubor *Elements. XML* pracovního postupu se refaktoruje při přejmenování nebo odstranění formuláře nebo při změně jeho cesty nasazení.|– Formulář se importuje, ale neodkazuje se na *elementy. XML* pracovního postupu.<br />– Soubor *Elements. XML* pracovního postupu není refaktored. **Poznámka:**  Pro tento scénář je nutné přidat a změnit pravidla a vlastnosti pro fungování.|
|Úloha|– Formulář je odkazován v souboru *Elements. XML* pracovního postupu.<br />– Soubor *Elements. XML* pracovního postupu není refaktored.|– Formulář se importuje, ale neodkazuje se na *elementy. XML* pracovního postupu.<br />– Soubor *Elements. XML* pracovního postupu není refaktored. **Poznámka:**  Pro tento scénář je nutné přidat a změnit pravidla a vlastnosti pro fungování.|
|Měně|Nelze použít. V Návrháři SharePoint nelze vytvořit formuláře změny ASPX.|Nelze použít. Formuláře úprav aplikace InfoPath nelze vytvořit v Návrháři služby SharePoint, s výjimkou integrovaného pracovního postupu serveru SharePoint, který není součástí souboru. wsp při exportu pracovního postupu.|

## <a name="see-also"></a>Viz také:
- [Návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Vytváření řešení pracovního postupu služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Import položek z existujícího webu služby SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)

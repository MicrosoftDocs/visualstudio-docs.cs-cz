---
title: Vytváření stránek pro SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 942891bc9281c07966160ea9df065408fcbfd5ff
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015171"
---
# <a name="create-pages-for-sharepoint"></a>Vytváření stránek pro SharePoint
  Můžete vytvářet stránky aplikace, stránky webu, stránky předlohy a rozložení stránek pro web služby SharePoint.

 Stránky aplikace můžete vytvořit pomocí šablony v aplikaci Visual Studio. Pomocí SharePoint designeru Vytvářejte stránky webu, stránky předlohy a rozložení stránek. Pak můžete tyto stránky importovat do sady Visual Studio, aby je bylo možné použít v projektu služby SharePoint.

 Vzhled a chování stránek můžete také upravit pomocí šablon stylů, ECMAScriptu a motivů.

## <a name="types-of-sharepoint-pages"></a>Typy stránek SharePoint
 Následující tabulka popisuje čtyři hlavní typy stránek, které obsahuje web služby SharePoint.

|Typ stránky|Popis|
|---------------|-----------------|
|Stránky aplikace|Stránku aplikace vytvořte, pokud chcete, aby stránka obsahovala vlastní kód, nebo chcete, aby se stránka sdílela ve více lokalitách. V opačném případě může být nejlepší volbou stránka webu.|
|Stránky webu|Stránku vytvořit web, pokud chcete provést některou z následujících úloh:<br /><br /> – Přidejte stránku do knihovny služby SharePoint.<br />– Povolí hostování funkcí této stránky, jako je například dynamická Webové části a zóny webových částí.<br />– Povolte uživatelům přizpůsobení stránky pomocí SharePoint designeru.<br /><br /> Nevytvářejte stránku webu, pokud chcete, aby stránka obsahovala vlastní kód. I když můžete přidat vlastní kód na stránku webu, kód se ukončí, když uživatel přizpůsobuje stránku pomocí SharePoint designeru.|
|Stránky předlohy|Pokud chcete definovat společnou strukturu stránek webu a stránek aplikace, vytvořte stránku předlohy.|
|Rozložení stránek|Rozložení stránek jsou specifická pro [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] a umožňují vám dále definovat společnou strukturu stránek webů a stránek aplikací.|

 Přehled každého typu stránky naleznete v tématech [stavební blok: stránky a uživatelské rozhraní](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)), [rozložení stránek a stránky předlohy](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Vytvořit stránky aplikace
 Můžete vytvořit stránky aplikace v aplikaci Visual Studio tak, že přidáte položku **stránky aplikace** do projektu služby SharePoint. Můžete přidat ovládací prvky na stránku a poté zpracovat události řízení přidáním kódu.

 Můžete nastavit zarážky v souboru kódu stránky, spustit ladicí program a otestovat stránku na místním webu služby SharePoint bez provedení jakýchkoli dalších kroků konfigurace. Další informace najdete v tématu [vytváření stránek aplikací pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Vytváření stránek webu, stránek předlohy a rozložení stránek
 Můžete vytvářet stránky webu, stránky předlohy a rozložení stránek pomocí služby SharePoint Designer. Pak můžete tyto stránky importovat do sady Visual Studio. Importujte své stránky, pokud chcete využít výhod nasazení nebo funkcí správy zdrojového kódu, které jsou k dispozici v aplikaci Visual Studio. Další informace naleznete v tématu [Import položek z existujícího webu služby SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Vzhledem k tomu, že je obtížné tyto stránky po importu importovat, je třeba navrhnout tyto stránky před jejich importem.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Vytváření kaskádových šablon stylů, ECMAScript a motivů
 Visual Studio neposkytuje šablony pro vývoj šablony stylů CSS (CSS), ECMAScript (JavaScript, JScript) nebo souborů motivů pro weby služby SharePoint. Tyto soubory můžete vytvořit pomocí pokynů, které jsou k dispozici v sadě SharePoint SDK nebo pomocí nástrojů, jako je například SharePoint Designer.

 Tyto soubory můžete do svého řešení přidat přímo nebo je můžete importovat. V obou případech je nutné vytvořit příslušné mapované složky pro každou položku, kterou přidáte. Další informace o tom, jak vytvořit mapovanou složku, naleznete v tématu [How to: Add and Remove mapované složky](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Další informace o vytváření šablony stylů CSS naleznete v tématu [šablony stylů CSS použití třídy v SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Další informace o vytváření souborů JavaScriptu a JScript pro řešení služby SharePoint naleznete v tématu [nastavení základní stránky ASPX pro ECMAScript](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Další informace o motivech naleznete v tématu [stavební blok: stránky a uživatelské rozhraní](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Vytváření stránek aplikací pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Popisuje postup přidání stránek aplikace: obsah *. aspx* , který je sloučen se stránkou předlohy služby SharePoint.|
|[Postupy: Vytvoření stránky aplikace](../sharepoint/how-to-create-an-application-page.md)|Ukazuje, jak vytvořit ASP.NET stránky, které běží na webu služby SharePoint.|
|[Návod: Vytvoření stránky aplikace služby SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Ukazuje, jak navrhnout a ladit webovou stránku ASP.NET pro web služby SharePoint.|

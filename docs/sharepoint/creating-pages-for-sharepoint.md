---
title: Vytváření stránek pro službu SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ecdbde69735f548b7ab70da132e9e2cc2080bbcb
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326047"
---
# <a name="create-pages-for-sharepoint"></a>Vytváření stránek pro službu SharePoint
  Můžete vytvořit stránky aplikací, weby, hlavní stránky a stránky rozložení pro web služby SharePoint.  
  
 Stránky aplikací můžete vytvořit pomocí šablony v sadě Visual Studio. Vytvořte weby, hlavní stránky a rozložení stránek s použitím návrháře služby SharePoint. Pak můžete importovat tyto stránek do sady Visual Studio jejich použití v projektu služby SharePoint.  
  
 Můžete také upravit vzhled a chování stránek pomocí kaskádových stylů, ECMAScript a motivů.  
  
## <a name="types-of-sharepoint-pages"></a>Typy stránek služby SharePoint
 Následující tabulka popisuje typy čtyři hlavní stránky, které obsahuje web služby SharePoint.  
  
|Typ stránky.|Popis|  
|---------------|-----------------|  
|Stránky aplikací|Pokud chcete stránku a obsahují vlastní kód, nebo chcete stránku sdílet mezi více lokalit, vytvoření stránky aplikace. Stránka serveru, jinak hodnota může být nejlepší volbou.|  
|Weby|Vytvoření stránky webu, pokud chcete provést některou z následujících úloh:<br /><br /> -Přidáte stránku do knihovny služby SharePoint.<br />-Aktivovat stránku a hostitelské funkce jako je například dynamické webové části a zóny webových částí.<br />-Povolte uživatelům umožnit přizpůsobení stránce pomocí návrháře služby SharePoint.<br /><br /> Pokud chcete na stránku a obsahovat vlastní kód, který není vytvoření stránky webu. I když můžete přidat vlastní kód na stránku lokality, kód zastaví spuštěn, když uživatel upravuje stránky pomocí seznamu služby SharePoint.|  
|Stránky předlohy|Vytvořte stránku předlohy, pokud chcete definovat běžné strukturu pro weby a stránky aplikací.|  
|Rozložení stránek|Rozložení stránek, které jsou specifické pro [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] a umožňují definovat další běžné strukturu pro weby a stránky aplikací.|  
  
 Přehled každý typ stránky najdete v tématu [stavebním blokem: stránek a uživatelské rozhraní](http://go.microsoft.com/fwlink/?LinkID=182095), a [rozložení stránky a stránky předlohy](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## <a name="create-application-pages"></a>Vytvoření stránky aplikací
 Stránky aplikací v sadě Visual Studio můžete vytvořit přidáním **stránky aplikace** položky projektu služby SharePoint. Můžete přidat ovládací prvky na stránku a pak zpracování události ovládacího prvku tak, že přidáte kód.  
  
 Nastavte zarážky v souboru kódu stránky, spuštění ladicího programu a testovací stránka na místní web služby SharePoint bez žádné další kroky konfigurace. Další informace najdete v tématu [vytváření stránek aplikací pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## <a name="create-site-pages-master-pages-and-page-layouts"></a>Vytvářet weby, hlavní stránky a rozložení stránek
 Weby, hlavní stránky a rozložení stránek můžete vytvořit pomocí návrháře služby SharePoint. Pak můžete importovat tyto stránek do sady Visual Studio. Importujte vaší stránky, pokud chcete využít výhod nasazení nebo zdroj ovládacího prvku funkce, které jsou k dispozici v sadě Visual Studio. Další informace najdete v tématu [import položek z existující stránky SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Protože je obtížné upravit tyto stránek po importu, měli byste tyto stránek navrhnout před jejich importem.  
  
## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Vytvoření šablony stylů CSS, ECMAScript a motivů
 Visual Studio neposkytuje šablony pro vývoj stylů CSS (Cascading Style), ECMAScript (JavaScript, JScript) nebo soubory motivu pro weby služby SharePoint. Tyto soubory můžete vytvořit pomocí pokyny, které jsou k dispozici v sadě SDK SharePoint nebo pomocí nástrojů, jako je například návrháře služby SharePoint.  
  
 Tyto soubory můžete přidat do řešení přímo nebo je můžete importovat. V obou případech musíte vytvořit odpovídající mapované složky pro každou položku, která přidáte. Další informace o tom, jak vytvořit mapované složky najdete v tématu [postupy: Přidání a odebrání mapovaných složek](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Další informace o vytváření šablony stylů CSS najdete v tématu [Cascading Style listy třída využití v SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Další informace o vytváření a používání jazyka JavaScript JScript soubory pro řešení služby SharePoint, naleznete v části [nastavení nahoru základní stránky ASPX pro ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Další informace o motivů najdete v tématu [stavebním blokem: stránek a uživatelské rozhraní](http://go.microsoft.com/fwlink/?LinkID=182095).  
  
## <a name="related-topics"></a>Související témata
  
|Název|Popis|  
|-----------|-----------------|  
|[Vytváření stránek aplikací pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Popisuje postup přidání stránky aplikací: *.aspx* obsah, který je sloučen s hlavní stránku služby SharePoint.|  
|[Postupy: vytvoření stránky aplikace](../sharepoint/how-to-create-an-application-page.md)|Ukazuje, jak vytvořit stránek ASP.NET, které běží na webu služby SharePoint.|  
|[Návod: Vytvoření stránky aplikace služby SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Ukazuje, jak navrhnout a ladit webové stránky ASP.NET pro web služby SharePoint.|  
  

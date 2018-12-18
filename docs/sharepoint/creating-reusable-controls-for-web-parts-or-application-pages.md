---
title: Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a621bb8c0f14cfb2c1869b98bb8bdbdd9c2d30bb
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327267"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací
  V sadě Visual Studio můžete vytvořit vlastní, opakovaně použitelné ovládací prvky, které mohou být spotřebovávána stránky aplikací a webových částí, které používají ve službě SharePoint. Tyto ovládací prvky se označují jako uživatelské ovládací prvky. Uživatelský ovládací prvek je druh složeného ovládacího prvku, který funguje podobně jako webovou stránku ASP.NET – můžete přidat existující ovládací prvky webového serveru a kód do uživatelského ovládacího prvku a definovat vlastnosti a metody pro ovládací prvek. Pak je můžete vložit do ASP.NET – webové stránky, kde budou fungovat jako jednotku.  
  
## <a name="create-a-user-control"></a>Vytvoření uživatelského ovládacího prvku
 Vytvoření uživatelského ovládacího prvku, přidejte **uživatelský ovládací prvek** k **prázdný projektu služby SharePoint**. Další informace najdete v tématu [postupy: vytvoření uživatelského ovládacího prvku pro část stránky nebo webové aplikace SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Když přidáte **uživatelský ovládací prvek** položky, Visual Studio vytvoří složku ve vašem projektu a potom přidá několik souborů do složky. Následující tabulka popisuje každý soubor.  
  
|Soubor|Popis|  
|----------|-----------------|  
|Soubor uživatelského ovládacího prvku|Definuje uživatelského ovládacího prvku. Návrh uživatelského ovládacího prvku tak, že přidáte ovládací prvky a značky do tohoto souboru.|  
|Souboru kódu|Obsahuje kód za uživatelského ovládacího prvku. Přidáte kód pro zpracování události do tohoto souboru.|  
|Soubor návrháře kódu|Obsahuje kód vygenerovaný návrháře a by neměla být upravována přímo.|  
  
## <a name="design-the-user-control"></a>Návrh uživatelského ovládacího prvku
 Návrh uživatelského ovládacího prvku pomocí návrháře Visual Web Developer v sadě Visual Studio. Tento návrhář se zobrazí při otevření souboru uživatelského ovládacího prvku ve vašem projektu a zvolte **návrhu** kartě.  

## <a name="consume-the-user-control"></a>Využívat uživatelského ovládacího prvku
 Uživatelské ovládací prvky ve službě SharePoint nezobrazí, dokud zahrnout je do stránky aplikace nebo webové části.  
  
 Chcete-li zahrnout uživatelského ovládacího prvku do stránky aplikace, otevřete webovou stránku, do které chcete přidat uživatelský ovládací prvek ASP.NET. Umožňuje přepnout do zobrazení návrhu, pak vyberte souboru vlastního uživatelského ovládacího prvku v Průzkumníku řešení a přetáhněte ji na stránce. Uživatelský ovládací prvek ASP.NET je přidán na stránku a návrháře vytvoří direktivy, který je nutný pro stránku rozpoznat uživatelského ovládacího prvku. Teď můžete pracovat s veřejné vlastnosti a metody ovládacího prvku.  
  
 Zahrnout uživatelský ovládací prvek webové části, přidat uživatelský ovládací prvek do webové části <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> kolekci do souboru kódu webové části. Následující příklad přidá uživatelský ovládací prvek na <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> kolekce webové části.  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debug-a-user-control"></a>Ladění uživatelského ovládacího prvku
 K ladění uživatelského ovládacího prvku, zkontrolujte, zda uživatelský ovládací prvek patří v stránky aplikace nebo webové části ve vašem projektu služby SharePoint. Můžete pak ladění kódu v uživatelského ovládacího prvku stejně, jako by ladění kódu v jakékoli projekt sady Visual Studio.  
  
 Při spuštění ladicího programu sady Visual Studio, Visual Studio otevře web služby SharePoint.  
  
 Ve službě SharePoint otevřete stránku aplikace, která zahrnuje uživatelského ovládacího prvku. Pokud uživatelský ovládací prvek je zahrnutý ve webové části, přidáte webovou část na stránku webové části ve službě SharePoint.  
  
 Další informace o ladění projektů služby SharePoint, naleznete v části [řešení řešení služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="related-topics"></a>Související témata
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: vytvoření uživatelského ovládacího prvku pro aplikace stránku nebo webovou část služby SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Ukazuje, jak vytvořit vlastní, opakovaně použitelné ovládací prvky, které mohou být spotřebovávána stránky aplikací a webových částí, které používají ve službě SharePoint.|  
  

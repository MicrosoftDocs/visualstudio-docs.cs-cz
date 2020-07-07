---
title: Vytváření opakovaně použitelných ovládacích prvků pro Webové části nebo stránky aplikace | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b174e1e16802838f19cec6dce727ea3199df730f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015140"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací
  V aplikaci Visual Studio můžete vytvořit vlastní, opakovaně použitelné ovládací prvky, které mohou být spotřebovány stránkami aplikace a Webové části, které běží na SharePointu. Tyto ovládací prvky se nazývají uživatelské ovládací prvky. Uživatelský ovládací prvek je druh složeného ovládacího prvku, který funguje podobně jako ASP.NET webová stránka – můžete přidat existující ovládací prvky webového serveru a značky k uživatelskému ovládacímu prvku a definovat vlastnosti a metody pro ovládací prvek. Pak je můžete vložit na ASP.NET webové stránky, kde se chovají jako jednotka.

## <a name="create-a-user-control"></a>Vytvoření uživatelského ovládacího prvku
 Chcete-li vytvořit uživatelský ovládací prvek, přidejte **uživatelský ovládací prvek** do **prázdného projektu služby SharePoint**. Další informace naleznete v tématu [Postupy: vytvoření uživatelského ovládacího prvku pro stránku aplikace služby SharePoint nebo webovou část](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).

 Když přidáte položku **uživatelského ovládacího prvku** , aplikace Visual Studio vytvoří složku v projektu a potom do složky přidá několik souborů. V následující tabulce jsou popsány jednotlivé soubory.

|Soubor|Popis|
|----------|-----------------|
|Soubor uživatelského ovládacího prvku|Definuje uživatelský ovládací prvek. Navrhněte uživatelský ovládací prvek přidáním ovládacích prvků a označením do tohoto souboru.|
|Soubor s kódem|Obsahuje kód za uživatelským ovládacím prvkem. Přidejte kód, který bude zpracovávat události do tohoto souboru.|
|Soubor s kódem návrháře|Obsahuje kód generovaný návrhářem a neměl by být přímo upravován.|

## <a name="design-the-user-control"></a>Návrh uživatelského ovládacího prvku
 Návrh uživatelského ovládacího prvku pomocí návrháře aplikace Visual Web Developer v aplikaci Visual Studio. Tento návrhář se zobrazí, když otevřete soubor uživatelského ovládacího prvku v projektu a kliknete na kartu **Návrh** .

## <a name="consume-the-user-control"></a>Využití uživatelského ovládacího prvku
 Uživatelské ovládací prvky se nezobrazí na SharePointu, dokud je nezahrnete na stránku aplikace nebo webovou část.

 Chcete-li do stránky aplikace zahrnout uživatelský ovládací prvek, otevřete webovou stránku, do které chcete přidat uživatelský ovládací prvek ASP.NET. Přepněte na zobrazení Návrh a pak v Průzkumník řešení vyberte vlastní soubor uživatelského ovládacího prvku a přetáhněte ho na stránku. Uživatelský ovládací prvek ASP.NET je přidán na stránku a návrhář vytvoří direktivu @ Register, která je požadována pro stránku k rozpoznání uživatelského ovládacího prvku. Nyní můžete pracovat s veřejnými vlastnostmi a metodami ovládacího prvku.

 Chcete-li do webové části zahrnout uživatelský ovládací prvek, přidejte uživatelský ovládací prvek do kolekce webových částí <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> v souboru kódu webové části. Následující příklad přidá uživatelský ovládací prvek do <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> kolekce webové části.

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>Ladění uživatelského ovládacího prvku
 Chcete-li ladit uživatelský ovládací prvek, ujistěte se, že uživatelský ovládací prvek je součástí stránky aplikace nebo webové části v projektu služby SharePoint. Potom můžete ladit kód v uživatelském ovládacím prvku stejně jako při ladění kódu v jakémkoli projektu sady Visual Studio.

 Když spustíte ladicí program sady Visual Studio, Visual Studio otevře web služby SharePoint.

 V SharePointu otevřete stránku aplikace, která obsahuje uživatelský ovládací prvek. Pokud je uživatelský ovládací prvek součástí webové části, přidejte webovou část na stránku webové části na SharePointu.

 Další informace o ladění projektů SharePoint naleznete v tématu [Poradce při potížích s řešeními služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: vytvoření uživatelského ovládacího prvku pro stránku aplikace SharePoint nebo webovou část](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Ukazuje, jak vytvořit vlastní, opakovaně použitelné ovládací prvky, které mohou být spotřebovány stránkami aplikace a Webové části, které běží na SharePointu.|

---
title: 'Postupy: definice a používání delegátů aktivit v Návrháři pracovních postupů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f99816153870884f868a6b229068bdc281408337
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865489"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Postupy: definice a používání delegátů aktivit v Návrháři postupu provádění
[!INCLUDE[net_v45](../includes/net-v45-md.md)] zahrnuje nové návrháře out-of-box <xref:System.Activities.Statements.InvokeDelegate> aktivity. Tento návrhář je možné přiřadit delegáty aktivity, které jsou odvozeny z <xref:System.Activities.ActivityDelegate>, jako například <xref:System.Activities.ActivityAction> nebo <xref:System.Activities.ActivityFunc%601>.  
  
### <a name="define-an-activity-delegate"></a>Definovat na delegáta aktivity  
  
1. V [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]vyberte **souboru**, **nový**, **projektu**. Vyberte **pracovního postupu** uzlu na levé straně a **Konzolová aplikace pracovního postupu** šablon na pravé straně. Název projektu (v případě potřeby) a klikněte na tlačítko **Ok**.  
  
2. Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **přidat**, **novou položku...** . Vyberte **pracovního postupu** uzlu na levé straně a **aktivity** šablon na pravé straně. Pojmenujte novou aktivitu **MyForEach.xaml** a klikněte na tlačítko **Ok**. Aktivity se otevře v Návrháři pracovních postupů.  
  
3. V Návrháři postupu provádění, klikněte **argumenty** kartu.  
  
4. Klikněte na tlačítko **vytvořit Argument**. Pojmenujte novou argument **položky**.  
  
5. V **typ argumentu** sloupci vyberte **pole [T]**.  
  
6. V typu prohlížeče, vyberte **objekt**. Klikněte na tlačítko **Ok**.  
  
7. Klikněte na tlačítko **vytvořit Argument** znovu. Pojmenujte novou argument **tělo**. V **směr** sloupci pro argument nový, vyberte **vlastnost**.  
  
8. Ve sloupci Typ argumentu vyberte **vyhledat typy...**  
  
9. V prohlížeči typu zadejte **ActivityAction** v **název typu** pole. Vyberte **ActivityAction\<T >** ve stromovém zobrazení. Vyberte **objekt** v rozevírací nabídce, která se zobrazí přiřadit typ **ActivityAction\<objektu >** na argument.  
  
10. Přetáhněte <xref:System.Activities.Statements.While> aktivita z **tok řízení** části panelu nástrojů na plochu návrháře.  
  
11. Vyberte <xref:System.Activities.Statements.While> aktivitu a vyberte **proměnné** kartu.  
  
12. Vyberte **vytvořit proměnnou**. Pojmenujte novou proměnnou **Index**.  
  
13. V **typ proměnné** sloupci vyberte **Int32**. Nechte **oboru** jako **při**a **výchozí** sloupce prázdné.  
  
14. Nastavte **podmínku** vlastnost <xref:System.Activities.Statements.While> aktivitu **index < Items.Length;**.  
  
15. Přetáhněte <xref:System.Activities.Statements.InvokeDelegate> aktivita z **primitiv** části panelu nástrojů **tělo** z <xref:System.Activities.Statements.While> aktivity.  
  
16. Vyberte **tělo** v rozevíracím seznamu delegáta.  
  
17. V **vlastnosti** mřížky <xref:System.Activities.Statements.InvokeDelegate> aktivity, klikněte na tlačítko **...** tlačítko **argumenty delegátů** vlastnost.  
  
18. V **hodnotu** sloupec argument s názvem **Argument**, zadejte **položky [Index]**. Klikněte na tlačítko **Ok** zavřete **DelegateArguments** dialogového okna.  
  
19. Přetáhněte <xref:System.Activities.Statements.Assign> aktivity na vodorovnou čáru pod <xref:System.Activities.Statements.InvokeDelegate> aktivity. <xref:System.Activities.Statements.Assign> Vytvoří aktivita a <xref:System.Activities.Statements.Sequence> aktivity se vytvoří automaticky tak, aby obsahovala dvě aktivity v **tělo** část **MyForEach** aktivity. Sekvence je vyžadováno, protože **tělo** oddíl může obsahovat pouze jednu aktivitu. Automaticky vytváří nové <xref:System.Activities.Statements.Sequence> aktivita je nová funkce [!INCLUDE[net_v45](../includes/net-v45-md.md)].  
  
20. Nastavte **k** vlastnost <xref:System.Activities.Statements.Assign> aktivitu **index**. Nastavte **hodnotu** vlastnost **přiřadit** aktivitu **index + 1**.  
  
    Vlastní **MyForEach** aktivit nyní vyvolá aktivitu libovolného jednou pro každou hodnotu předanou do něj prostřednictvím **položky** kolekce s hodnotami v kolekci jako vstupy pro aktivitu.  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>Použití vlastní aktivity v pracovním postupu  
  
1. Sestavte projekt stisknutím kombinace kláves **Ctrl + Shift + B**.  
  
2. V **Průzkumníka řešení**, otevřete **Workflow1.xaml** v návrháři.  
  
3. Přetáhněte **MyForEach** aktivitu z panelu nástrojů na plochu návrháře. Aktivita bude v části nástrojů se stejným názvem jako projekt.  
  
4. Nastavte **položky** vlastnost **MyForEach** aktivitu **nové Object [] {1, "abc"}**.  
  
5. Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivita z **primitiv** části panelu nástrojů **delegáta: Body** část **MyForEach** aktivity.  
  
6. Nastavte **Text** vlastnost <xref:System.Activities.Statements.WriteLine> aktivitu **Argument.ToString()**.  
  
   Při spuštění pracovního postupu se zobrazí konzole následující:  
  
   **1**   
   **abc**
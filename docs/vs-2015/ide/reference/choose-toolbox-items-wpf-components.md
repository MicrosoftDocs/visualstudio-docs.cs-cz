---
title: Zvolit položky panelu nástrojů, součásti WPF | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c04a5f4be811c7cb1cae525ef0a16b437dd88b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887134"
---
# <a name="choose-toolbox-items-wpf-components"></a>Výběr položek sady nástrojů, součásti WPF
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Tato karta **zvolit položky nástrojů** dialogové okno zobrazí seznam dostupných ovládacích prvků Windows Presentation Foundation (WPF) v místním počítači. Chcete-li zobrazit tento seznam, vyberte **zvolit položky nástrojů** z **nástroje** nabídku zobrazíte **zvolit položky nástrojů** dialogové okno a pak vyberte jeho **WPF Součásti** kartu. Součástí uvedené seřadit, vyberte libovolné záhlaví sloupce.  
  
- Pokud je zaškrtnuto políčko vedle komponenty, bude zobrazena ikona pro danou součást v **nástrojů**.  
  
  > [!TIP]
  >  Chcete-li přidat instanci ovládacího prvku WPF do projektu dokument otevřený pro úpravy, přetáhněte jeho **nástrojů** ikonu na návrhovou plochu zobrazení. Výchozí značky a pro součásti jsou vloženy do svého projektu můžete upravit. Další informace najdete v tématu [postupy: Správa okna nástrojů](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2) a [postupy: manipulace s karty panelu nástrojů](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
- Pokud je zrušeno zaškrtnutí políčka vedle komponenty, příslušnou ikonu se odebere z **sady nástrojů.**  
  
  > [!NOTE]
  >  Součásti rozhraní .NET Framework nainstalované v počítači nadále k dispozici, zda jsou ikony pro ně zobrazí **nástrojů**.  
  
  Sloupce **součásti WPF** karta obsahovat následující informace:  
  
  Název  
  Seznamy názvů ovládacích prvků WPF pro položky, které existují v registru počítače.  
  
  Obor názvů  
  Zobrazuje hierarchii [NIB: Knihovna tříd rozhraní .NET Framework](http://msdn.microsoft.com/en-us/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) obor názvů, který definuje strukturu komponenty. Výsledky můžete řadit podle sloupce seznam součástí, které jsou v každém oboru názvů rozhraní .NET Framework nainstalované v počítači k dispozici.  
  
  Název sestavení  
  Zobrazí název sestavení rozhraní .NET Framework, který obsahuje obor názvů pro jednotlivé komponenty. Výsledky můžete řadit podle sloupce do seznamu oborů názvů obsažené v každé sestavení rozhraní .NET Framework nainstalované v počítači.  
  
  Adresář  
  Zobrazí umístění sestavení rozhraní .NET Framework. Je výchozím umístěním pro všechna sestavení do globální mezipaměti sestavení. Další informace o globální mezipaměti sestavení, naleznete v tématu [práce se sestaveními a s globální pamětí sestavení](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Filtr**  
 Filtruje seznam ovládacích prvků WPF na základě řetězce, které zadáte do textového pole. Jsou uvedeny všechny shody z kteréhokoli čtyři sloupce.  
  
 **Vymazat**  
 Vymaže řetězec filtru.  
  
 **Procházet**  
 Otevře **otevřít** dialogové okno, které vám umožní přejít do sestavení, které obsahují ovládací prvky WPF. Použijte k načtení sestavení, které nejsou umístěné v globální mezipaměti sestavení.  
  
 **Jazyk**  
 Ukazuje lokalizovaného jazyka sestavení, který obsahuje vybraný ovládací prvek WPF.  
  
## <a name="limitations"></a>Omezení  
 Přidání vlastního ovládacího prvku nebo <xref:System.Windows.Controls.UserControl> do panelu nástrojů má následující omezení.  
  
- Platí jenom pro vlastní ovládací prvky, které jsou definovány mimo aktuální projekt.  
  
- Nelze aktualizovat správně při změně konfigurace řešení v ladicí verzi nebo z verze pro ladění. Je to proto, že odkaz není odkaz na projekt, ale místo toho je pro sestavení na disku. Pokud je ovládací prvek součástí aktuálního řešení, když změníte z ladicí verze, váš projekt i nadále odkazují na ladicí verze ovládacího prvku.  
  
  Kromě toho pokud metadat v době návrhu platí pro vlastní ovládací prvek a tato metadata Určuje, že <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> je nastavena na `false`, ovládací prvek se nezobrazí v panelu nástrojů.  
  
  Ovládací prvky přímo v XAML zobrazení můžete odkazovat pomocí mapování oboru názvů a sestavení pro ovládací prvek. Další informace najdete v tématu [jak: importovat do XAML Namespace](http://msdn.microsoft.com/en-us/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).  
  
## <a name="see-also"></a>Viz také  
 [Zvolte dialogové okno položky panelu nástrojů (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [Panel nástrojů](../../ide/reference/toolbox.md)   
 [Postupy: použití ovládacího prvku WPF třetích stran v aplikaci WPF](http://msdn.microsoft.com/en-us/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)




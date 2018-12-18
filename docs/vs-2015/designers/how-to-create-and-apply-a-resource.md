---
title: Vytvoření a použití prostředku | Dokumentace Microsoftu
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
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ef5dc15db983a54e60df447a2457d9dbc6804d85
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915800"
---
# <a name="how-to-create-and-apply-a-resource"></a>Vytvoření a použití prostředku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Styly a šablony pro elementy v Návrháři XAML jsou uloženy v opakovaně použitelné entity nazývané prostředky. Styly umožňují nastavit vlastnosti elementu a použít tato nastavení pro jednotný vzhled napříč více prvků. A [ControlTemplate](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.aspx) definuje vzhled ovládacího prvku a mohou být použity také jako prostředek. Další informace najdete v tématu [rychlý start: používání stylů pro ovládací prvky](http://go.microsoft.com/fwlink/?LinkID=248239) a [rychlý start: řízení šablony](http://go.microsoft.com/fwlink/?LinkID=247982).  
  
 Při každém vytvoření nového prostředku z existující vlastnosti [styl](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx), nebo `ControlTemplate`, **vytvořit prostředek** dialogové okno umožňuje definovat prostředek na úrovni aplikace, úrovni dokumentu nebo na úrovni prvku. Tyto úrovně určit, kde lze prostředek použít. Například pokud definujete prostředek na úrovni prvku, prostředek je použít jenom na element, na kterém jste vytvořili. Také lze zvolit uložení prostředku do adresáře zdrojů, což je oddělený soubor, který lze znovu použít v jiném projektu.  
  
### <a name="to-create-a-new-resource"></a>Chcete-li vytvořit nový prostředek  
  
1.  S XAML soubor otevřen v Návrháři XAML vytvořte element nebo zvolte prvek v okně osnovy dokumentu.  
  
2.  V okně Vlastnosti zvolte značku vlastnosti, které se zobrazí jako symbol políčka napravo od hodnoty vlastnosti, a klikněte na tlačítko **převést na nový prostředek**. Symbol bílé pole určuje výchozí hodnotu a symbol černé skříňky obvykle značí, že použití místního prostředku  
  
     Zobrazí se příslušné dialogové okno pro tvorbu prostředku. Při vytváření prostředku ze štětce, zobrazí se toto dialogové okno:  
  
     ![Vytvořit prostředek – dialogové okno](../designers/media/xaml-create-resource.png "xaml_create_resource")  
  
3.  V **název (klíč)** zadejte název klíče. Toto je název, který vám pomůže při dalších prvků, které odkazují na prostředek.  
  
4.  V části **definovat v**, zvolte možnost, která určuje, kde chcete prostředek, který chcete definovat:  
  
    -   Chcete-li být prostředek dostupný libovolnému dokumentu v aplikaci, zvolte **aplikace**.  
  
    -   Chcete-li být prostředek přístupný pouze v aktuálním dokumentu, zvolte **tento dokument**.  
  
    -   Chcete-li být prostředek přístupný pouze na prvek z jste vytvořili prostředek nebo na jeho podřízené prvky, zvolte **tento dokument**a v rozevíracím seznamu vyberte *element*: *název* .  
  
    -   Chcete-li definovat prostředek v souboru slovníku prostředků, který lze opětovně použít v jiných projektech, klikněte na tlačítko **slovník prostředků**a potom vyberte existující soubor slovníku prostředků, jako je například **StandardStyles.xaml**, v rozevíracím seznamu.  
  
5.  Zvolte **OK** tlačítko má prostředek vytvořit a použít ji k elementu, ze kterého jste vytvořili.  
  
### <a name="to-apply-a-resource-to-an-element-or-property"></a>Chcete-li použít prostředek na element nebo vlastnost  
  
1. V okně Osnova dokumentu zvolte prvek, který má být použita prostředku.  
  
2. Proveďte jednu z těchto akcí:  
  
   - Použití prostředku na vlastnost. V okně Vlastnosti vyberte značka vlastnosti vedle hodnoty vlastností, vyberte **místního prostředku** nebo **systémový prostředek**a pak zvolte ze seznamu, který se zobrazí dostupné zdroje.  
  
      Pokud nevidíte prostředek, který byste měli vidět, může to být způsobeno typ prostředku neodpovídá typu vlastnosti.  
  
   - Platí pro ovládací prvek prostředku šablony stylů nebo ovládací prvek. Otevřete místní nabídku pro ovládací prvek v okno osnovy dokumentu, zvolte **upravit šablonu** nebo **upravit další šablony**, zvolte **aplikovat zdroj**a klikněte na tlačítko Název šablony ovládací prvek ze zobrazeného seznamu.  
  
     > [!NOTE]
     >  **Úprava šablony** se používá k aplikování šablon ovládacích prvků. **Upravit další šablony** se používá k aplikování jiné typy šablon.  
  
     Prostředky je možné použít bez ohledu na to jsou kompatibilní. Například prostředek štětce lze použít u **popředí** vlastnost <xref:Windows.UI.Xaml.Controls.TextBox> ovládacího prvku.  
  
### <a name="to-edit-a-resource"></a>Chcete-li upravit prostředek  
  
1.  Vyberte prvek na návrhové ploše nebo v okně osnovy dokumentu.  
  
2.  Zvolte výchozí nebo místní vlastnost značky vpravo od vlastnosti v okně Vlastnosti a pak zvolte **upravit prostředek** otevřít **upravit prostředek** dialogové okno.  
  
3.  Změna možností pro prostředek.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření uživatelského rozhraní pomocí Návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)




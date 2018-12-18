---
title: Úpravy stylu objektů v Blendu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ae494a82e92086cfa0e8e2a69b7f7eee022807a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917199"
---
# <a name="modify-the-style-of-objects-in-blend"></a>Úpravy stylu objektů v Blendu

Nejjednodušší způsob, jak přizpůsobit objekt je v nastavit vlastnosti **vlastnosti** podokně.

Pokud chcete znovu použít nastavení nebo skupiny nastavení, vytvořte opakovaně použitelné prostředek. To může být *styl*, *šablony*, nebo něco jednoduše jako vlastních barev. Můžete také nastavit zobrazení ovládacího prvku odlišně v závislosti na jeho stav. Například změní zelené tlačítko, po kliknutí na jeho.

## <a name="brushes-modify-the-appearance-of-an-object"></a>Štětce: Upravit vzhled objektu

Použití štětce k objektu, pokud chcete změnit její vzhled.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Malovat opakující se bitovou kopii nebo vzor objektu

Malovat pomocí bitové kopie nebo vzor objektu s opakováním *dlaždici štětce*.

Pokud chcete vytvořit štětce dlaždice, začněte vytvořením *obrázek štětce*, *kreslení štětce*, nebo *visual štětce* prostředků.

Vytvořte štětce bitovou kopii pomocí obrázku. Následující ilustrace znázorňuje štětce bitové kopie, štětce bitové kopie na dlaždicích a štětce image obráceně.

![Obrázek štětce](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![štětce Mage vedle sebe](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![Překlopení štětce bitové kopie](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

Vytvořte kreslení štětce s použitím vektoru kreslení například cestu nebo tvar. Následující ilustrace znázorňuje kreslení štětce, kreslení štětce rozložen formou dlaždic a kreslení štětce obráceně.

![Kreslení štětce](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![Kreslení štětce vedle sebe](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![Kreslení štětce obráceně](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

Vytvořte visual štětce z ovládací prvek tlačítko. Následující ilustrace znázorňuje visual štětce a visual štětce rozložen formou dlaždic.

![Visual štětce](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![Visual štětce vedle sebe](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>Styly a šablony: vytvoření konzistentní vzhled a chování napříč ovládací prvky

Můžete navrhnout vzhled a chování ovládacího prvku jednou a jiných ovládacích prvků použití tohoto návrhu tak, aby je nemuseli individuálně, zachovat.

**Můžete použít styl?** : Pokud chcete nastavit výchozí vlastnosti (například barvu tlačítko), použijte *styl*. I když jste použili styl k němu můžete upravit ovládacího prvku.

**Měli byste použít šablonu?** : Pokud chcete změnit strukturu ovládacího prvku, použijte *šablony*. Představte si převodu obrázek nebo logo na tlačítko. Ovládací prvek nelze změnit po použití šablony na ni.

### <a name="create-a-template-or-style"></a>Vytvořit šablonu ani styl

Už existuje dva způsoby, jak vytvořit šablonu. Jakýkoli objekt můžete převést na vaše návrhové plochy do ovládacího prvku nebo šablony můžete založit na existujícího ovládacího prvku.

Převést na šablonu řízení všech objektů, vyberte objekt a pak na **nástroje** nabídce zvolte **zkontrolujte do ovládacího prvku**.

Pokud chcete založit na ovládací prvek stávající šablony, vyberte objekt, na návrhové plochy. Pak v horní části návrhové plochy, zvolte tlačítko s popisem cesty a potom vyberte **upravit šablonu**a potom zvolte **úpravě kopie** nebo **vytvořit prázdnou**.

![Upravit šablonu nabídky](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

Chcete-li vytvořit styl, vyberte objekt a potom v **objekt** nabídce zvolte **upravit styl**a potom vyberte **úpravě kopie** nebo **vytvořit prázdnou**.

- Zvolte **úpravě kopie** začínat výchozí styl nebo šablony ovládacího prvku.

- Zvolte **vytvořit prázdnou** spustit od začátku.

**Upravit aktuální** možnost se zobrazí pouze v případě, že upravíte styl nebo šablonu, kterou jste už vytvořili. Nezobrazí se pro ovládací prvek, který stále používá výchozí šablona služby systému.

V **vytvořit prostředek stylu** dialogové okno, můžete buď pojmenovat styl nebo šablony tak, aby můžete použít později, nebo můžete použít styl nebo šablonu pro všechny ovládací prvky tohoto typu.

![Vytvořit styl prostředek – dialogové okno](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> Nelze vytvořit styly nebo šablon pro každý typ ovládacího prvku. Pokud je nepodporuje ovládacího prvku, se nezobrazí tlačítko s popisem cesty výše návrhové plochy.
> Chcete-li vrátit úpravy rozsahu hlavního dokumentu, klikněte na tlačítko **vrátit obor** ![vrátit obor ikonu](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png).

### <a name="apply-a-style-or-template-to-a-control"></a>Použít styl nebo šablony do ovládacího prvku

Klikněte pravým tlačítkem na objekt v [objekty a časový horizont](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-objects-and-timeline-panel) panelu, vyberte **upravit šablonu**a potom zvolte **použít prostředků**.

![Použití prostředků nabídky](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>Obnovit výchozí styl nebo šablony ovládacího prvku

Vyberte ovládací prvek a v [vlastnosti](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-properties-panel) panelu, vyhledejte **styl** nebo **šablony** vlastnost. Zvolte **rozšířené možnosti**a potom klikněte na **resetovat** v místní nabídce.

## <a name="visual-states-change-the-appearance-of-a-control-based-on-its-state"></a>Visual stavy: Změna vzhledu ovládacího prvku na základě jeho stavu

Ovládací prvky může mít různé visual vzhledy na základě interakcí uživatele. Například můžete použít tlačítko Zapnout zelený, když uživatel klikne ji nebo ji můžete spustit animace. Zkraťte nebo prodloužit doba mezi visual stavy pomocí přechody.

![Ukazatele stavu myši](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**Podívejte se na krátké video:** ![tlačítko Přehrát akci](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Správa stavu ovládacích prvků WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>Prostředky: Vytvoření barvy, styly a šablony a opakovaném

Můžete převést jakoukoli ve vašem projektu a prostředek. Prostředek se právě objekt, který můžete opakovaně použít na různých místech v aplikaci. Můžete například vytvořit barvu jednou, nastavte ho prostředku a potom použít na několik objektů. Chcete-li změnit barvu všech těchto objektů, právě změňte barvu prostředků.

![Převést barvu pro tlačítko prostředků](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![Vytvořit prostředek barev – dialogové okno](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>Viz také

- [Vytvoření uživatelského rozhraní pomocí nástroje Blend pro Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
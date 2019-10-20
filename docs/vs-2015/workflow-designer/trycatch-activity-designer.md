---
title: Návrhář aktivity TryCatch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b26bb37d1ddeabb77b1399c6cbce5ae55b59702c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654663"
---
# <a name="trycatch-activity-designer"></a>Návrhář aktivity TryCatch
Návrhář aktivity **TryCatch** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.TryCatch>.

## <a name="the-trycatch-activity"></a>Aktivita TryCatch
 Aktivita <xref:System.Activities.Statements.TryCatch> obsahuje aktivitu <xref:System.Activities.Statements.TryCatch.Try%2A>, kolekci **\<TException Catch >** a aktivitu <xref:System.Activities.Statements.TryCatch.Finally%2A>. @No__t_0 typu **TException** obsahuje <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> a <xref:System.Activities.Statements.Catch%601.Action%2A>. Společně se používají k implementaci typického mechanismu zpracování chyb na základě výjimek. Aktivita <xref:System.Activities.Statements.TryCatch> se pokusí spustit aktivitu <xref:System.Activities.Statements.TryCatch.Try%2A>. Pokud aktivita <xref:System.Activities.Statements.TryCatch.Try%2A> vyvolá jakoukoli výjimku, <xref:System.Activities.Statements.TryCatch> aktivita použije její kolekci **Catch < TException \>** ke spárování s výjimkou. Pokud existuje shoda, pak je proveden <xref:System.Activities.Statements.Catch%601.Action%2A> odpovídajícího **> \<TException catch** , který slouží jako logika zpracování chyb pro výjimku. Pokud se aktivity v oddílu <xref:System.Activities.Statements.TryCatch.Try%2A> úspěšně dokončí nebo se aktivity v <xref:System.Activities.Statements.TryCatch.Catches%2A> úspěšně dokončí, <xref:System.Activities.Statements.TryCatch> aktivita spustí svou <xref:System.Activities.Statements.TryCatch.Finally%2A> aktivitu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][výjimky](https://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136).

### <a name="using-the-trycatch-activity-designer"></a>Pomocí návrháře aktivity TryCatch
 Návrhář aktivity **TryCatch** lze najít v kategorii **zpracování chyb** v **sadě nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte **panel nástrojů** z  **Nabídka zobrazení** nebo CTLR + ALT + X.)

 Návrhář aktivity **TryCatch** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.TryCatch> s výchozím <xref:System.Activities.Activity.DisplayName%2A> TryCatch. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivity **TryCatch** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti musí být upraveny na povrchu návrháře aktivity **TryCatch** .

 Kliknutím na tlačítko Rozbalit v pravém horním rohu návrháře **TryCatch** se v rozbaleném zobrazení zobrazí pole **Try**, **catch**a **finally** . Pokud chcete přidat catch, klikněte na tlačítko **Přidat nové catch** v **TryCatch** designeru. Tlačítko se změní na pole se seznamem typu. Vyberte typ výjimky a stisknutím klávesy ENTER přidejte catch. Po přidání **catch**se oblast catch rozbalí a aktivita může být vyřazena do catch pro definování logiky spuštění pro catch. Všimněte si, že na pravé straně rozbalené oblasti catch je textové pole. Proměnnou výjimky můžete pojmenovat pomocí tohoto textového pole. Proměnnou výjimky lze použít pouze pro aktivity v rámci stejného **catch**.

 Návrhář **TryCatch** nepodporuje úpravy **catch**. Pokud chcete změnit typ výjimky, je nutné odstranit **catch** a přidat nový. **Catch** se dá odstranit tak, že ho vyberete a odstraníte nebo pomocí nabídky **Odstranit** v kontextové nabídce, ke které se dostanete kliknutím pravým tlačítkem.

### <a name="the-trycatch-properties"></a>Vlastnosti TryCatch
 Následující tabulka ukazuje <xref:System.Activities.Statements.TryCatch>properties a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje nepovinný popisný název aktivity <xref:System.Activities.Statements.TryCatch>. Výchozí hodnota je TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Aktivita se poprvé spustí při spuštění <xref:System.Activities.Statements.TryCatch>.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Kolekce elementů **catch** , které mají být zkontrolovány, pokud aktivita <xref:System.Activities.Statements.TryCatch.Try%2A> vyvolá výjimku.<br /><br /> Potřebujete alespoň přidat jednu aktivitu do <xref:System.Activities.Statements.TryCatch.Catches%2A> nebo aktivitu v bloku <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Aktivita, která se má provést, když <xref:System.Activities.Statements.TryCatch.Try%2A> a všechny potřebné aktivity v kolekci <xref:System.Activities.Statements.TryCatch.Catches%2A> dokončí provádění.<br /><br /> Potřebujete alespoň přidat jednu aktivitu do <xref:System.Activities.Statements.TryCatch.Catches%2A> nebo aktivitu v bloku <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>Viz také
 [Vyvolání](../workflow-designer/throw-activity-designer.md) opětovného [vyvolání](../workflow-designer/rethrow-activity-designer.md) [kolekce](../workflow-designer/collection-activity-designers.md)
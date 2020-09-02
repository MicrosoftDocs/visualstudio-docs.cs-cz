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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654663"
---
# <a name="trycatch-activity-designer"></a>Návrhář aktivity TryCatch
Návrhář aktivity **TryCatch** slouží k vytvoření a konfiguraci <xref:System.Activities.Statements.TryCatch> aktivity.

## <a name="the-trycatch-activity"></a>Aktivita TryCatch
 <xref:System.Activities.Statements.TryCatch>Aktivita obsahuje <xref:System.Activities.Statements.TryCatch.Try%2A> aktivitu, kolekci **Catch \<TException> ** a <xref:System.Activities.Statements.TryCatch.Finally%2A> aktivitu. <xref:System.Activities.Statements.Catch%601>Typ **TException** obsahuje <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> a <xref:System.Activities.Statements.Catch%601.Action%2A> . Společně se používají k implementaci typického mechanismu zpracování chyb na základě výjimek. <xref:System.Activities.Statements.TryCatch>Aktivita se pokusí provést aktivitu <xref:System.Activities.Statements.TryCatch.Try%2A> . Pokud <xref:System.Activities.Statements.TryCatch.Try%2A> Aktivita vyvolá jakoukoli výjimku, <xref:System.Activities.Statements.TryCatch> aktivita použije svou kolekci **catch<TException \> ** , aby se shodovala s výjimkou. Pokud existuje shoda, pak <xref:System.Activities.Statements.Catch%601.Action%2A> je proveden odpovídající ** \<TException> catch** , který slouží jako logika zpracování chyb pro výjimku. Pokud aktivity v <xref:System.Activities.Statements.TryCatch.Try%2A> oddílu úspěšně dokončí nebo aktivity <xref:System.Activities.Statements.TryCatch.Catches%2A> úspěšně dokončeny, <xref:System.Activities.Statements.TryCatch> aktivita spustí svou <xref:System.Activities.Statements.TryCatch.Finally%2A> aktivitu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Výjimky](https://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136).

### <a name="using-the-trycatch-activity-designer"></a>Pomocí návrháře aktivity TryCatch
 Návrhář aktivity **TryCatch** lze najít v kategorii **zpracování chyb** v **sadě nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTLR + ALT + X).

 Návrhář aktivity **TryCatch** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu, kde jsou obvykle umístěny aktivity, například uvnitř a <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.TryCatch> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> TryCatch. <xref:System.Activities.Activity.DisplayName%2A>Hodnotu lze upravit v záhlaví návrháře aktivity **TryCatch** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti musí být upraveny na povrchu návrháře aktivity **TryCatch** .

 Kliknutím na tlačítko Rozbalit v pravém horním rohu návrháře **TryCatch** se v rozbaleném zobrazení zobrazí pole **Try**, **catch**a **finally** . Pokud chcete přidat catch, klikněte na tlačítko **Přidat nové catch** v **TryCatch** designeru. Tlačítko se změní na pole se seznamem typu. Vyberte typ výjimky a stisknutím klávesy ENTER přidejte catch. Po přidání **catch**se oblast catch rozbalí a aktivita může být vyřazena do catch pro definování logiky spuštění pro catch. Všimněte si, že na pravé straně rozbalené oblasti catch je textové pole. Proměnnou výjimky můžete pojmenovat pomocí tohoto textového pole. Proměnnou výjimky lze použít pouze pro aktivity v rámci stejného **catch**.

 Návrhář **TryCatch** nepodporuje úpravy **catch**. Pokud chcete změnit typ výjimky, je nutné odstranit **catch** a přidat nový. **Catch** se dá odstranit tak, že ho vyberete a odstraníte nebo pomocí nabídky **Odstranit** v kontextové nabídce, ke které se dostanete kliknutím pravým tlačítkem.

### <a name="the-trycatch-properties"></a>Vlastnosti TryCatch
 V následující tabulce jsou uvedeny <xref:System.Activities.Statements.TryCatch> vlastnosti a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Určuje nepovinný popisný název <xref:System.Activities.Statements.TryCatch> aktivity. Výchozí hodnota je TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|Ne|Aktivita se poprvé spustila, když se <xref:System.Activities.Statements.TryCatch> spustí.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|Ne|Kolekce elementů **catch** , které mají být zkontrolovány, pokud <xref:System.Activities.Statements.TryCatch.Try%2A> Aktivita vyvolá výjimku.<br /><br /> V bloku potřebujete alespoň přidat jednu aktivitu <xref:System.Activities.Statements.TryCatch.Catches%2A> nebo aktivitu <xref:System.Activities.Statements.TryCatch.Finally%2A> .|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|Ne|Aktivita, která má být provedena v případě, že jsou <xref:System.Activities.Statements.TryCatch.Try%2A> dokončeny všechny potřebné aktivity v <xref:System.Activities.Statements.TryCatch.Catches%2A> kolekci.<br /><br /> V bloku potřebujete alespoň přidat jednu aktivitu <xref:System.Activities.Statements.TryCatch.Catches%2A> nebo aktivitu <xref:System.Activities.Statements.TryCatch.Finally%2A> .|

## <a name="see-also"></a>Viz také
 [Vyvolání](../workflow-designer/throw-activity-designer.md) opětovného [vyvolání](../workflow-designer/rethrow-activity-designer.md) [kolekce](../workflow-designer/collection-activity-designers.md)
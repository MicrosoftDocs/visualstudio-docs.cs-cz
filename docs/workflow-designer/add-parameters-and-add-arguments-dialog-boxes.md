---
title: Návrhář postupu provádění - přidat parametry a přidat argumenty dialogových oknech
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- AddParameters.UI
ms.assetid: a21fb4fe-134b-40b0-8497-86b842940ca1
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 1b01e08ee5579f5422e8e51562444302d685d58d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789041"
---
# <a name="add-parameters-and-add-arguments-dialog-boxes"></a>Dialogová okna Přidat parametry a Přidat argumenty

Následující tabulka popisuje prvky uživatelského rozhraní (UI) **přidat parametry** dialogové okno používané <xref:System.Activities.Statements.InvokeMethod> návrháře:

|||
|-|-|
|**Směr**|Určuje, zda parametr představuje tok dat do metody mimo metodu, nebo obojí.|
|**Typ**|Název typu nový parametr.|
|**Hodnota**|Výraz jazyka Visual Basic, kterého chcete přiřadit nový parametr výchozí hodnotu|

Následující tabulka popisuje prvky uživatelského rozhraní (UI) **Přidat argumenty** dialogové okno používané <xref:System.Activities.Statements.InvokeDelegate> návrháře:

|||
|-|-|
|**Jméno**|Název argumentu.|
|**Směr**|Určuje, zda argument představuje tok dat do delegáta z delegáta nebo obojí.|
|**Typ**|Název typu argumentu nové.|
|**Hodnota**|Hodnota se použije pro tuto instanci argument delegáta.|
---
title: Stránka možnosti, vlastnosti uzlu písma a barvy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23aa4eff3339ad3cd3ab7d4106745dc6fa83df34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662429"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Stránka Možnosti, vlastnosti uzlu Písmo a barvy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tento dokument popisuje vlastnosti písma a barvy pro panel nástrojů, který je zaregistrován pro zobrazení v části **písma a barvy** v kategorii **prostředí** dialogového okna **Možnosti** . To podporuje dynamickou povahu skupin barev, které se mohou změnit, pokud jsou sady VSPackage nainstalovány nebo odinstalovány.

 Následující část ukazuje příklad registrovaného typu okna a vlastností, které jsou k dispozici pro každé okno.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Textový editor nebo panely nástrojů a dialogová okna
 `DTE.Properties("FontsAndColors", "TextEditor")`

 -nebo-

 `DTE.Properties("FontsAndColors", "Printer")`

 -nebo-

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|FontFamily|Get/Set (String)|Název písma, který se má použít, například "Courier New".|
|FontCharacterSet|Get/Set ( <xref:EnvDTE.vsFontCharSet> )|<xref:EnvDTE.vsFontCharSet>Hodnota, která určuje typ znakové sady, která se má použít, například hebrejština nebo ruština.|
|FontSize|Získat nebo nastavit (krátký)|Velikost písma, která se má použít, v bodech Například 10 nebo 12.|

## <a name="see-also"></a>Viz také
 [Řízení nastavení možností](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [Určení názvů položek vlastností na](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) stránce Možnosti stránky možnosti [, vlastnosti uzlu prostředí](../../ide/reference/options-page-environment-node-properties.md) [, vlastnosti uzlu textový editor](../../ide/reference/options-page-text-editor-node-properties.md)

---
title: Stránka Možnosti, vlastnosti uzlu barev a písem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 538711a72a1f22a9dfd984f6fcd36ea7787742f6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296061"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Stránka Možnosti, vlastnosti uzlu Písmo a barvy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Tento dokument popisuje vlastnosti písma a barvy pro panel nástrojů, která je zaregistrovaná a může se zobrazí v rámci **písma a barvy** v **prostředí** kategorii **možnosti** Dialogové okno. Tento atribut podporuje dynamické povaze skupiny, které lze zabarvit položek, které můžete změnit, pokud budou instalovat nebo odinstalovat rozšíření VSPackages.  
  
 Následující část popisuje příklad typ registrované okna a vlastnosti, které jsou k dispozici pro každé okno.  
  
## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Textový Editor nebo tiskárnu nebo dialogových oken a nástroj pro Windows  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 -nebo-  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 -nebo-  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|Název položky vlastnosti|Hodnota|Popis|  
|------------------------|-----------|-----------------|  
|fontFamily|Získá nebo nastaví (String)|Název písma, které chcete použít, jako je například "New Kurýrní."|  
|FontCharacterSet|Získá nebo nastaví (<xref:EnvDTE.vsFontCharSet>)|A <xref:EnvDTE.vsFontCharSet> hodnotu určující typ znakovou sadu, jako je například hebrejština nebo ruština.|  
|Velikost písma|Získá nebo nastaví (krátký)|Velikost písma pro použití v bodech. Například 10 nebo 12.|  
  
## <a name="see-also"></a>Viz také  
 [Řízení nastavení možností](http://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Určování názvů položky vlastností na stránkách možností](http://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Stránka Možnosti, vlastnosti uzlu prostředí](../../ide/reference/options-page-environment-node-properties.md)   
 [Stránka Možnosti, vlastnosti uzlu Textový editor](../../ide/reference/options-page-text-editor-node-properties.md)




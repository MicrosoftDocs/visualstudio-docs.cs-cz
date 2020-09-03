---
title: Zprostředkovatel symbolů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6af1af9d2e178241fa8a5957e18c1a5333fa4b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178891"
---
# <a name="symbol-provider"></a>Poskytovatel symbolů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Implementace vyhodnocovacího filtru výrazů musí přistupovat k symbolickým ladicím informacím generovaným kompilátorem jazyka, aby bylo možné vyhodnotit proměnné a výrazy. Udělá to tak, že zabírají rozhraní zprostředkovatele symbolů (SP), označovaného také jako obslužná rutina symbolu.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poskytuje SPs pro spravovaný kód i nativní kód pomocí formátu souboru symbolů databáze programu (PDB). Pokud nepotřebujete, aby váš program používal symboly uložené ve vlastním formátu, doporučuje se použít SPs, který poskytuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="implementation-notes"></a>Poznámky k implementaci  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Ladicí stroje od verze modulu CLR (Common Language Runtime) očekávají, že mluví se službou SPS. V důsledku toho musí být v rámci SP, který bude pracovat s ladicími moduly sady Visual Studio, podporován modul CLR. Úplný seznam všech rozhraní ladění CLR najdete v debugref.doc, který je součástí [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] .  
  
 Pokud bude vaše aktualizace SP fungovat jenom s vaším vlastním ladicím modulem, můžete implementovat SP podle toho, jak se bude zobrazovat podle potřeb vašeho ladicího stroje.  
  
## <a name="see-also"></a>Viz také  
 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)

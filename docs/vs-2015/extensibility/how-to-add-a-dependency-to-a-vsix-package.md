---
title: 'Postupy: Přidání závislosti do balíčku VSIX | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 997c0df133b72d69dfb4e69de53a1b77e1a0965c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697509"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Postupy: Přidání závislosti k balíčku VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nastavit nasazení balíčku VSIX, které nainstaluje všechny závislosti, které ještě nejsou k dispozici v cílovém počítači. Chcete-li to provést, zahrňte do souboru source. extension. vsixmanifest závislosti VSIX.  
  
#### <a name="to-add-a-dependency"></a>Přidání závislosti  
  
1. Otevřete soubor source. extension. vsixmanifest v zobrazení **Návrh** . Přejděte na kartu **závislosti** a klikněte na **Nový**.  
  
2. Přidání nainstalovaného rozšíření: v dialogovém okně **Přidat novou závislost** vyberte možnost **nainstalovaná rozšíření** a potom v rozevíracím seznamu **název**vyberte rozšíření v seznamu.  
  
3. Chcete-li přidat další VSIX, který není nainstalován:: v dialogovém okně **Přidat novou závislost** vyberte **soubor v systému souborů** a poté pomocí tlačítka **Procházet** vyberte VSIX.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu rozšíření VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Příprava rozšíření pro nasazení Instalační služby systému Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)

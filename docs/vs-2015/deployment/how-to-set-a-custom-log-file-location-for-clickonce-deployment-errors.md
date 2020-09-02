---
title: 'Postupy: nastavení vlastního umístění souboru protokolu pro chyby nasazení ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a1b7c93e4b30bbfd373a5fad9d7001452d4f587
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795939"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Postupy: Nastavení vlastního umístění souboru protokolu pro chyby nasazení ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] udržuje soubory protokolu aktivace pro všechna nasazení. Tyto protokoly dokumentují všechny chyby, které se týkají instalace a inicializace [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení. Ve výchozím nastavení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vytvoří jeden soubor protokolu pro každou aktivaci nasazení. Tyto soubory protokolu se uloží do složky dočasných internetových souborů. Soubor protokolu pro nasazení se uživateli zobrazí, když dojde k selhání aktivace a uživatel klikne na **Podrobnosti** v dialogovém okně výsledné chyby.  
  
 Toto chování můžete změnit pro konkrétního klienta pomocí Editoru registru (**regedit.exe**) a nastavit tak vlastní cestu k souboru protokolu. V takovém případě [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] protokoluje úspěšné a neúspěšné aktivace pro všechna nasazení v jednom souboru.  
  
> [!CAUTION]
> Pokud používáte Editor registru nesprávně, může dojít k vážným problémům, které mohou vyžadovat přeinstalaci operačního systému. Editor registru použijte na vlastní riziko.  
  
> [!NOTE]
> Soubor protokolu bude někdy potřeba zkrátit nebo odstranit, aby se zabránilo jeho většímu růstu.  
  
 Následující postup popisuje, jak nastavit vlastní umístění souboru protokolu pro jednoho klienta.  
  
### <a name="to-set-a-custom-log-file-location"></a>Nastavení vlastního umístění souboru protokolu  
  
1. Otevřete **Regedit.exe**.  
  
2. Přejděte k uzlu `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. Nastavte hodnotu řetězce `LogFilePath` na úplnou cestu a název souboru upřednostňovaného vlastního umístění protokolu.  
  
     Toto umístění musí být v adresáři, ke kterému má uživatel oprávnění k zápisu. Například v systému Windows Vista vytvořte následující strukturu složek a nastavte `LogFilePath` ji na C:\Users \\<UserName \> \Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží s nasazením ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)

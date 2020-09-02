---
title: Monitorování globálních nastavení pomocí Správce textu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ece51450b8344ae4715a912399ec538171a26a5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695459"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Použití textového správce k monitorování globálního nastavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud implementujete základní editor, je nutné sledovat změny provedené v globálním nastavení, protože tyto změny mohou ovlivnit vaši instanci editoru. Změny můžete sledovat při naslouchání událostem, které vyvolala správce textu. Pokud například zadáte globální preference pro vzhled nebo chování komponenty v základním editoru, jako je například datový objekt dokumentu, nástroj text uloží tyto informace a oznámí všem postiženým klientům.  
  
## <a name="text-manager-functions"></a>Funkce Správce textu  
 Správce textu vyvolá události pro určitý počet nastavení, včetně následujících:  
  
- Zda je vyrovnávací paměť v rámci správy zdrojového kódu  
  
- Postup registrace pro oznámení o změnách souborů  
  
- Jak udržet přehled o tom, která zobrazení jsou přidružená k určitým vyrovnávacím pamětem  
  
- Předvolby barevného zabarvení textu  
  
- Předvolby tabulátoru a prostoru  
  
  Předvolby, které jsou jedinečné pro daný jazyk, nejsou spravovány správcem textu. Tato nastavení musí spravovat jednotlivé jazykové služby.  
  
  Oznámení o události pro správce textu je zajištěno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> rozhraním. Implementací tohoto rozhraní do objektu klienta můžete zpracovávat události vyvolané správcem textu. Zaregistrujete se na tyto události pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> rozhraní ve Správci textu.  
  
## <a name="see-also"></a>Viz také  
 [Uvnitř základního editoru](../extensibility/inside-the-core-editor.md)   
 [Funkce editoru](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)

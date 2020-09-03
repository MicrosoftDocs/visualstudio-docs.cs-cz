---
title: Přístup k uloženým písmům a nastavením barev | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821828"
---
# <a name="accessing-stored-font-and-color-settings"></a>Přístup k uloženým nastavením písem a barev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Integrované vývojové prostředí (IDE) ukládá upravená nastavení pro písma a barvy v registru. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>Pro přístup k těmto nastavením můžete použít rozhraní.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Inicializace trvalého stavu písem a barev  
 Informace o písmech a barvách jsou uloženy podle kategorie v následujícím umístění registru: [HKCU\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<CategoryGUID>* ], kde *\<CategoryGUID>* je identifikátor GUID kategorie.  
  
 Proto pro zahájení Persistence musí VSPackage:  
  
- Získejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní voláním `QueryService` u poskytovatele globální služby.  
  
     `QueryService` musí být volána pomocí argumentu ID služby `SID_SVsFontAndColorStorage` a argument ID rozhraní `IID_IVsFontAndColorStorage` .  
  
- Použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodu k otevření kategorie, která se má zachovat, pomocí identifikátoru GUID kategorie a příznaku Mode jako argumentů.  
  
  Režim určený `fFlags` argumentem je vytvořen z hodnot ve <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> výčtu. Tento režim řídí:  

  - Nastavení, která lze použít prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní.  

  - Buď všechna nastavení, nebo pouze ta, která uživatelé upraví a které lze získat prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní.  

  - Způsob, jakým se změny nastavení uživatele šíří.  

  - Formát hodnot barvy, které se používají.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Použití trvalého stavu písma a barev  
 Zachování písma a barev zahrnuje:  
  
- Synchronizace nastavení IDE s nastavením uloženým v registru.  
  
- Rozšiřování informací o změně registru.  
  
- Nastavení a načtení nastavení uložených v registru.  
  
  Synchronizace nastavení úložiště s nastavením IDE je z velké části transparentní. Příslušné integrované vývojové prostředí (IDE) automaticky zapisuje aktualizované nastavení pro **zobrazení položek** do položek registru kategorií.  
  
  Pokud více rozhraní VSPackage sdílí určitou kategorii, VSPackage by měl vyžadovat, aby byly generovány události, když <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> se k úpravě uložených nastavení registru použijí metody rozhraní.  
  
  Ve výchozím nastavení není generování událostí povoleno. Chcete-li povolit generování událostí, je nutné otevřít kategorii pomocí <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> . To způsobí, že rozhraní IDE bude volat odpovídající <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> metodu, kterou VSPackage implementuje.  
  
> [!NOTE]
> Úpravy na stránce vlastností **Font a Color** generují události nezávislé na <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Rozhraní lze použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> k určení, zda je zapotřebí aktualizace písma a nastavení barev v mezipaměti před voláním metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> třídy.  
  
### <a name="storing-and-retrieving-information"></a>Ukládání a načítání informací  
 Chcete-li získat nebo nakonfigurovat informace, které může uživatel upravit pro pojmenovanou položku pro zobrazení v otevřené kategorii, sady VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> volají <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> metody a.  
  
 Informace o atributech písma konkrétní kategorie jsou získány pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> metod a.  
  
> [!NOTE]
> `fFlags`Argument, který je předán <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodě při otevření této kategorie, definuje chování <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metody a. Ve výchozím nastavení tyto metody vrací pouze informace aboutdisplay itemsthat se změnily. Pokud je však kategorie otevřena pomocí <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> příznaku, jsou aktualizovány i změněny položky zobrazení, ke kterým lze použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> .  
  
 Ve výchozím nastavení se v registru uchovávají jenom informace o změněných **položkách zobrazení** . <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>Rozhraní nelze použít k načtení všech nastavení pro písma a barvy.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> Metody a vrací REGDB_E_KEYMISSING, (0x80040152L), když je použijete k načtení informací o nezměněných **položkách zobrazení**.  
  
 Nastavení všech **položek zobrazení** v určité **kategorii** lze získat pomocí metod `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` rozhraní.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementace vlastních kategorií a položek zobrazení](../extensibility/implementing-custom-categories-and-display-items.md)

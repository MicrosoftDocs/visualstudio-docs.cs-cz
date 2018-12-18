---
title: Přístup k uložené písma a barev | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 953f74b309d8dc147d04d86b843f138002de972f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910677"
---
# <a name="access-stored-font-and-color-settings"></a>Přístup uložená nastavení písma a barvy
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Integrované vývojové prostředí (IDE) ukládá změny nastavení písem a barev v registru. Můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní pro přístup k nastavení.

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>K zahájení trvalost stavu písma a barvy
 Písma a barvy informace jsou uloženy podle kategorií v následujícím umístění registru: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<verze sady Visual Studio >* \FontAndColors\\  *\<CategoryGUID >*], kde  *\<CategoryGUID >* je kategorie identifikátor GUID.

 Proto zahájíte trvalost VSPackage musí:

-   Získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní voláním `QueryService` proti globální poskytovatel.

     `QueryService` musí být volána pomocí argumentu služby ID `SID_SVsFontAndColorStorage` a interface ID argument `IID_IVsFontAndColorStorage`.

-   Použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodu otevření kategorie natrvalo pomocí identifikátoru GUID kategorii a příznak režimu jako argumenty.

     Režimu určeném `fFlags` argument, je vytvořen z hodnot v <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> výčtu. Tento režim – ovládací prvky:

    -   Nastavení, která je přístupná prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní.

    -   Všechna nastavení nebo jen nastavení, která uživatelé upravovat a, které jsou získat prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní.

    -   Metody šíření změn nastavení pro uživatele.

    -   Formát hodnot barev, které se používají.

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Použití trvalost stavu písma a barvy
 Zachování písma a barvy zahrnuje:

- Synchronizace nastavení prostředí IDE s nastaveními uloženými v registru.

- Přenos informací o úpravy registru.

- Nastavení nebo načtení nastavení uložené v registru.

  Synchronizace nastavení úložiště se nastavení rozhraní IDE je z velké části transparentní. Základní rozhraní IDE automaticky zapíše aktualizované nastavení pro **zobrazit položky** položky registru kategorií.

  Pokud více rozšíření VSPackages sdílet určité kategorie, VSPackage by od vás vyžadovat, že jsou generovány události při metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní se používají pro úpravy nastavení registru uložené.

  Ve výchozím nastavení není povolené generování události. Pokud chcete povolit generování události, kategorii musí otevřeli pomocí <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Otevírání kategorii způsobí, že rozhraní IDE volat odpovídající <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> metody, která implementuje VSPackage.

> [!NOTE]
>  Změny pomocí **písma a barvy** stránku vlastností generovat události, které jsou nezávislé na <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> rozhraní k určení, zda aktualizace mezipaměti nastavení písem a barev je potřeba před voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> třídy.

### <a name="store-and-retrieve-information"></a>Store a načítání informací
 Chcete-li získat nebo konfigurovat informace, které uživatel může změnit pro položku s názvem zobrazení otevřít kategorie, zavolejte rozšíření VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> metody.

 Informace o písma atributy pro určité kategorie je získat pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> metody.

> [!NOTE]
>  `fFlags` Argument, který je předán <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodu, když se otevřel dané kategorie definuje chování <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metody. Ve výchozím nastavení tyto metody vrací pouze informace o zobrazit položky, které se změnily. Nicméně pokud kategorie se otevře pomocí <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> příznak, jak aktualizovat a beze změny viditelné položky je možný přes <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.

 Ve výchozím nastavení, měnit jenom **zobrazit položky** informace se ukládají v registru. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Rozhraní nelze použít k načtení všech nastavení písem a barev.

> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metody vrací REGDB_E_KEYMISSING (0x80040152L) při použití k načtení informací o beze změny **zobrazit položky**.

 Nastavení všech **zobrazit položky** v konkrétní **kategorie** můžete získat pomocí metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> rozhraní.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [Implementovat vlastní kategorie a zobrazení položek](../extensibility/implementing-custom-categories-and-display-items.md)
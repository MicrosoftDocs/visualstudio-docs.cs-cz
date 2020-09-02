---
title: Přehled řešení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb3bb85ab172404262c147cce285cebaf756afc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831854"
---
# <a name="solutions-overview"></a>Přehled řešení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Řešení je seskupení jednoho nebo více projektů, které spolupracují při vytváření aplikace. Informace o projektu a stavu týkající se řešení jsou uloženy ve dvou různých souborech řešení. Soubor řešení (. sln) je založen na textu a lze jej umístit pod správu zdrojového kódu a sdílet mezi uživateli. Soubor možnosti uživatele řešení (. suo) je binární. V důsledku toho nemůže být soubor. suo umístěn pod správou zdrojového kódu a obsahuje informace specifické pro uživatele.  
  
 Libovolný VSPackage může zapisovat do obou typů souborů řešení. Vzhledem k povaze souborů jsou k zápisu do nich k dispozici dvě různá rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>Rozhraní zapisuje textové informace do souboru. sln a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> rozhraní zapisuje binární proudy do souboru. suo.  
  
> [!NOTE]
> Projekt nemusí explicitně zapisovat položku pro sebe sama do souboru řešení; prostředí zpracovává projekt. Proto pokud nechcete přidat další obsah konkrétně do souboru řešení, nemusíte tímto způsobem registrovat VSPackage.  
  
 Každé rozhraní VSPackage podporující trvalé trvalosti používá tři rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> rozhraní, které je implementováno prostředím a voláno pomocí VSPackage a `IVsPersistSolutionProps` a `IVsPersistSolutionOpts` , které jsou implementovány rozhraním VSPackage. `IVsPersistSolutionOpts`Rozhraní musí být implementováno pouze v případě, že je do souboru. suo zapisovány soukromé informace.  
  
 Po otevření řešení dojde k následujícímu procesu.  
  
1. Prostředí toto řešení přečte.  
  
2. Pokud prostředí najde a `CLSID` , načte odpovídající VSPackage.  
  
3. Pokud se načte VSPackage, prostředí vyvolá rozhraní pro `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> rozhraní, které VSPackage vyžaduje.  
  
   1. Při čtení ze souboru. sln volá prostředí `QueryInterface` pro `IVsPersistSolutionProps` .  
  
   2. Při čtení ze souboru. suo volá prostředí `QueryInterface` pro `IVsPersistSolutionOpts` .  
  
   Konkrétní informace týkající se použití těchto souborů najdete v [řešení (. SLN)](../../extensibility/internals/solution-dot-sln-file.md) – možnosti uživatele pro soubor a [řešení (. Suo) soubor](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
> Chcete-li vytvořit novou konfiguraci řešení skládající se ze dvou konfigurací projektů a s výjimkou třetího ze sestavení, je nutné použít uživatelské rozhraní stránky vlastností nebo automatizaci. Nemůžete změnit konfigurace správce sestavení řešení a jejich vlastnosti přímo, ale můžete manipulovat s řešením správce sestavení pomocí `SolutionBuild` třídy z DTE v modelu automatizace. Další informace o konfiguraci řešení najdete v tématu věnovaném [konfiguraci řešení](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>

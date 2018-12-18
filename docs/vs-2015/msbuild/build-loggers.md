---
title: Protokolovací nástroje sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbf27388013b71945879537dffff1e53a7314e7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853235"
---
# <a name="build-loggers"></a>Protokolovací nástroje sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Protokolovací nástroje poskytují způsob, jak můžete upravit výstupní sestavení a zobrazení zprávy, chyby nebo upozornění v reakci na události v konkrétním sestavení. Každý protokolovacího nástroje je implementován jako třída rozhraní .NET, která implementuje <xref:Microsoft.Build.Framework.ILogger> rozhraní, která je definována v sestavení Microsoft.Build.Framework.dll.  
  
 Existují dvě metody, které můžete použít při implementaci protokolovač:  
  
- Implementace <xref:Microsoft.Build.Framework.ILogger> rozhraní přímo.  
  
- Odvodit třídu z pomocná třída <xref:Microsoft.Build.Utilities.Logger>, která je definovaná v sestavení Microsoft.Build.Utilities.dll. <xref:Microsoft.Build.Utilities.Logger> implementuje <xref:Microsoft.Build.Framework.ILogger> a poskytuje výchozí implementaci některých <xref:Microsoft.Build.Framework.ILogger> členy.  
  
  Toto téma vysvětluje, jak napsat jednoduchý protokolovací nástroj, který je odvozen z <xref:Microsoft.Build.Utilities.Logger>, a zobrazí zprávy v konzole v reakci na určité události sestavení.  
  
## <a name="registering-for-events"></a>Registrace k událostem  
 Účelem protokolovací nástroj je shromažďování informací o průběhu sestavení udávaný modul sestavení a potom nahlásit těchto informací užitečným způsobem. Všechny Protokolovací nástroje musí přepsat <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metodu, která je, kde se registruje protokolovací nástroj pro události. V tomto příkladu protokolovací nástroj zaregistruje <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, a <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> události.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#2)]  
  
## <a name="responding-to-events"></a>Reagování na události  
 Teď, když protokolovacího nástroje je zaregistrovaný pro konkrétní události, je potřeba zpracovat tyto události, které se objeví. Pro <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, a <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> události, protokolovacího nástroje je zapíše jednoduše, krátké fráze a název souboru projektu zahrnutý v události. Všechny zprávy z protokolovací nástroj se zapisují do okna konzoly.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#3)]  
  
## <a name="responding-to-logger-verbosity-values"></a>Reakce na hodnoty podrobnost protokolování  
 V některých případech můžete chtít pouze protokolování informací z události, pokud MSBuild.exe **/verbosity** přepínač obsahuje určitou hodnotu. V tomto příkladu <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> obslužné rutiny události pouze zaznamená zprávu, pokud <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> vlastnost, která se nastavuje přes **/verbosity** přepnout, je rovna <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed`.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#4)]  
  
## <a name="specifying-a-logger"></a>Určení protokolovací nástroj  
 Jakmile protokolovacího nástroje je zkompilovat do sestavení, je třeba sdělit [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] používat tento protokolovač během sestavení. To se provádí pomocí **/logger** přepínači s MSBuild.exe. Další informace o přepínačích, které jsou k dispozici pro MSBuild.exe, naleznete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).  
  
 Následující příkaz sestaví projekt `MyProject.csproj` a používá třídu protokolovacího nástroje implementované v `SimpleLogger.dll`. **/Nologo** přepínač Zobrazovat nápis a zprávu o autorských právech a **/noconsolelogger** přepínač zakáže výchozí [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] protokolovací nástroj konzoly.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 Následující příkaz sestaví projekt se stejným protokolovací nástroj, ale s `Verbosity` úroveň `Detailed`.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad obsahuje kompletní kód pro protokolovacího nástroje.  
  
### <a name="code"></a>Kód  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#1)]  
  
### <a name="comments"></a>Komentáře  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje, jak implementovat protokolovací nástroj, který zapíše protokol do souboru místo zobrazení v okně konzoly.  
  
### <a name="code"></a>Kód  
 [!code-csharp[msbuild_BasicLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_BasicLogger/CS/msbuild_BasicLogger.cs#1)]  
  
### <a name="comments"></a>Komentáře  
  
## <a name="see-also"></a>Viz také  
 [Získávání protokolů o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)




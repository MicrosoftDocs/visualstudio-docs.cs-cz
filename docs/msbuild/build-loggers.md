---
title: Protokolovací nástroje sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e1faf28c05dec58117e5d34e21e7c8020ad3a4d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894284"
---
# <a name="build-loggers"></a>Protokolovací nástroje sestavení
Protokolovací nástroje poskytují způsob, jak můžete upravit výstupní sestavení a zobrazení zprávy, chyby nebo upozornění v reakci na události v konkrétním sestavení. Každý protokolovacího nástroje je implementován jako třída rozhraní .NET, která implementuje <xref:Microsoft.Build.Framework.ILogger> rozhraní, která je definována v *Microsoft.Build.Framework.dll* sestavení.  
  
 Existují dvě metody, které můžete použít při implementaci protokolovač:  
  
- Implementace <xref:Microsoft.Build.Framework.ILogger> rozhraní přímo.  
  
- Odvodit třídu z pomocná třída <xref:Microsoft.Build.Utilities.Logger>, který je definován v *Microsoft.Build.Utilities.dll* sestavení. <xref:Microsoft.Build.Utilities.Logger> implementuje <xref:Microsoft.Build.Framework.ILogger> a poskytuje výchozí implementaci některých <xref:Microsoft.Build.Framework.ILogger> členy.  
  
  Toto téma vysvětluje, jak napsat jednoduchý protokolovací nástroj, který je odvozen z <xref:Microsoft.Build.Utilities.Logger>, a zobrazí zprávy v konzole v reakci na určité události sestavení.  
  
## <a name="register-for-events"></a>Zaregistrovat se na události  
 Účelem protokolovací nástroj je shromažďování informací o průběhu sestavení udávaný modul sestavení a potom nahlásit těchto informací užitečným způsobem. Všechny Protokolovací nástroje musí přepsat <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metodu, která je, kde se registruje protokolovací nástroj pro události. V tomto příkladu protokolovací nástroj zaregistruje <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, a <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> události.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## <a name="respond-to-events"></a>Reakce na události  
 Teď, když protokolovacího nástroje je zaregistrovaný pro konkrétní události, je potřeba zpracovat tyto události, které se objeví. Pro <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, a <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> události, protokolovacího nástroje je zapíše jednoduše, krátké fráze a název souboru projektu zahrnutý v události. Všechny zprávy z protokolovací nástroj se zapisují do okna konzoly.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## <a name="respond-to-logger-verbosity-values"></a>Reakce na hodnoty podrobnost protokolování  
 V některých případech můžete chtít pouze protokolování informací z události, pokud MSBuild.exe **-podrobností** přepínač obsahuje určitou hodnotu. V tomto příkladu <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> obslužné rutiny události pouze zaznamená zprávu, pokud <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> vlastnost, která se nastavuje přes **-podrobností** přepnout, je rovna <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed`.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## <a name="specify-a-logger"></a>Zadejte protokolovací nástroj  
 Jakmile protokolovacího nástroje je zkompilovat do sestavení, je třeba sdělit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] používat tento protokolovač během sestavení. To se provádí pomocí **-protokolovací nástroj** přepínači s *MSBuild.exe*. Další informace o přepínačích, které jsou k dispozici pro *MSBuild.exe*, naleznete v tématu [odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md).  
  
 Následující příkaz sestaví projekt *MyProject.csproj* a používá třídu protokolovacího nástroje implementované v *SimpleLogger.dll*. **- Nologo** přepínač Zobrazovat nápis a zprávu o autorských právech a **- noconsolelogger** přepínač zakáže výchozí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] protokolovací nástroj konzoly.  
  
```cmd  
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll  
```  
  
 Následující příkaz sestaví projekt se stejným protokolovací nástroj, ale s `Verbosity` úroveň `Detailed`.  
  
```cmd  
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed  
```  

## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad obsahuje kompletní kód pro protokolovacího nástroje.  
  
### <a name="code"></a>Kód  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje, jak implementovat protokolovací nástroj, který zapíše protokol do souboru místo zobrazení v okně konzoly.  
  
### <a name="code"></a>Kód  
 [!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
## <a name="see-also"></a>Viz také:  
 [Získání protokolů o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
---
title: Sestavení úhozů kláves | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a00bbb8ce239275ff140dbedf2157e4cdc41d44c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634523"
---
# <a name="build-loggers"></a>Sestavení úhozů kláves

Úhozy kláves poskytují způsob, jak přizpůsobit výstup sestavení a zobrazit zprávy, chyby nebo upozornění v reakci na konkrétní události sestavení. Každý protokolovací nástroj je implementován <xref:Microsoft.Build.Framework.ILogger> jako třída .NET, která implementuje rozhraní, které je definováno v sestavení *Microsoft.Build.Framework.dll.*

Existují dva přístupy, které můžete použít při implementaci protokolování:

- Implementujte <xref:Microsoft.Build.Framework.ILogger> rozhraní přímo.
- Odvodit třídu z <xref:Microsoft.Build.Utilities.Logger>pomocné třídy , která je definována v sestavení *Microsoft.Build.Utilities.dll.* <xref:Microsoft.Build.Utilities.Logger>implementuje <xref:Microsoft.Build.Framework.ILogger> a poskytuje výchozí <xref:Microsoft.Build.Framework.ILogger> implementace některých členů.

  Toto téma bude vysvětlovat, jak napsat <xref:Microsoft.Build.Utilities.Logger>jednoduchý protokolovací nástroj, který je odvozen od aplikace a zobrazí zprávy v konzole v reakci na určité události sestavení.

## <a name="register-for-events"></a>Registrace na akce

Účelem protokolování je shromažďovat informace o průběhu sestavení, jak je hlášena modulu sestavení a potom sestavy těchto informací užitečným způsobem. Všechny úhozy <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> kláves musí přepsat metodu, což je, kde protokolování registruje pro události. V tomto příkladu protokolování <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>registruje pro , <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>a <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> události.

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>Reagovat na události

Nyní, když je protokolování registrováno pro konkrétní události, je třeba zpracovat tyto události, když k nim dojde. Pro <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> a události logger jednoduše zapíše krátkou frázi a název souboru projektu zapojených do události. Všechny zprávy z protokolování jsou zapsány do okna konzoly.

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>Reagovat na hodnoty podrobností protokolování

V některých případech můžete chtít pouze protokolovat informace z události, pokud přepínač MSBuild.exe **-verbosity** obsahuje určitou hodnotu. V <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> tomto příkladu obslužná rutina události zaznamená zprávu pouze v <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> případě, že vlastnost, která je nastavena přepínačem **-verbosity,** je rovna <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed`.

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>Určení protokolovacího nástroje

Jakmile je protokolovací nástroj zkompilován do sestavení, musíte msbuild sdělit, aby tento protokolovací nástroj používal během sestavení. To se provádí pomocí přepínače **-logger** s *msbuild.exe*. Další informace o přepínačích dostupných pro *soubor MSBuild.exe*naleznete v [tématu Odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md).

Následující příkazový řádek vytvoří projekt *MyProject.csproj* a používá třídu logger implementovanou v *souboru SimpleLogger.dll*. Přepínač **-nologo** skryje banner a zprávu o autorských právech a přepínač **-noconsolelogger** zakáže výchozí logger konzoly MSBuild.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Následující příkazový řádek vytvoří projekt se stejným protokolovacím protokolem, ale s `Verbosity` úrovní `Detailed`.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad obsahuje úplný kód pro protokolování.

### <a name="code"></a>kód

[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje, jak implementovat protokolovací nástroj, který zapíše protokol do souboru, nikoli jeho zobrazení v okně konzoly.

### <a name="code"></a>kód

[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>Viz také

- [Získat protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)

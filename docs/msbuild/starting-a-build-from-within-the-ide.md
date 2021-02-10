---
title: Spuštění sestavení z prostředí IDE | Microsoft Docs
description: Naučte se, jak pomocí Microsoft. VisualStudio. Shell. Interop. IVsBuildManagerAccessor začít sestavovat sestavení pro vlastní projektové systémy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ee685ebf542dbf9405afce8cfdf5c4a7e060b79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956045"
---
# <a name="start-a-build-from-within-the-ide"></a>Spuštění sestavení z integrovaného vývojového prostředí (IDE)

Vlastní projektové systémy musí použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor> ke spuštění sestavení. Tento článek popisuje důvody tohoto požadavku a popisuje postup.

## <a name="parallel-builds-and-threads"></a>Paralelní sestavení a vlákna

 Visual Studio umožňuje paralelní sestavení, které vyžaduje, aby bylo možné získat přístup k běžným prostředkům. Systémy projektu mohou spustit sestavení asynchronně, ale tyto systémy nesmí volat funkce sestavení v rámci zpětného volání.

 Pokud systém projektu mění proměnné prostředí, musí nastavit NodeAffinity sestavení na OutOfProc. Tento požadavek znamená, že nemůžete použít objekty hostitele, protože vyžadují uzel v rámci proc.

## <a name="use-ivsbuildmanageraccessor"></a>Použití IVSBuildManagerAccessor

 Následující kód popisuje metodu, kterou může projektový systém použít ke spuštění sestavení:

```csharp

public bool Build(Project project, bool isDesignTimeBuild)
{
    // Get the accessor from the IServiceProvider interface for the
    // project system
    IVsBuildManagerAccessor accessor =
        serviceProvider.GetService(typeof(SVsBuildManagerAccessor)) as
        IVsBuildManagerAccessor;
    bool releaseUIThread = false;
    try
    {
        if(accessor != null)
        {
            // Claim the UI thread under the following conditions:
            // 1. The build must use a resource that uses the UI thread
            // or,
            // 2. The build requires the in-proc node AND waits on the
            // UI thread for the build to complete
            if(NeedsUIThread)
            {
                int result = accessor.ClaimUIThreadForBuild();
                if(result != S_OK)
                {
                     // Not allowed to claim the UI thread right now
                     return false;
                }
                releaseUIThread = true;
             }
             if(isDesignTimeBuild)
             {
// Start the design time build
                  int result = accessor.BeginDesignTimeBuild();
                  if(result != S_OK)
                  {
                      // Not allowed to begin a design-time build at
                      // this time. Try again later.
                      return false;
                  }
             }
         }
         bool buildSucceeded = false;
         // perform project-system specific build set up tasks
         // Create your BuildRequestData
         // This assumes a IHostServices variable (hostServices) set
   // to your host services. If you don't use a project instance
         // (you build from a file for example) then use another
         // constructor.
         BuildRequestData requestData = new
             BuildRequestData(project.CreateProjectInstance(),
             "myTarget", hostServices,
             BuildRequestData.BuildRequestDataFlags.None);
         // Mark your your submission as Pending
         BuildSubmission submission =
              BuildManager.DefaultBuildManager.
              PendBuildRequest(requestData);
         // Register the loggers in BuildLoggers
         if (accessor != null)
         {
               foreach (ILogger logger in BuildLoggers)
               {
                    accessor.RegisterLogger(submission.SubmissionId,
                        logger);
               }
         }
         BuildResult buildResult = submission.Execute();
         return buildResult;
     }
     // Clean up resources
     finally
     {
         if(accessor != null)
         {
             // Unregister the loggers, if necessary.
             accessor.UnregisterLoggers(submission.SubmissionId);
             // Release the UI thread, if used
             if(releaseUIThread)
             {
                  accessor.ReleaseUIThreadForBuild();
             }
             // End the design time build, if used
             if(isDesignTimeBuild)
             {
                  accessor.EndDesignTimeBuild();
             }
         }
     }
}
```

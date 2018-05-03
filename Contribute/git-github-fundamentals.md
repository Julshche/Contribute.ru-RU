---
title: Основные сведения о Git и GitHub для создания документации
description: В этой статье приводятся общие сведения о репозиториях Git в GitHub, принципах организации содержимого и правилах именования, используемых для сайта docs.microsoft.com.
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 06/30/2017
ms.prod: non-product-specific
ms.topic: contributor-guide
ms.custom: external-contributor-guide
ms.openlocfilehash: 5f7f90b69953e23833906202c739d2168b139d7e
ms.sourcegitcommit: 3ec397fab57ea582edb03a59609f62d886410ee8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2018
---
# <a name="git-and-github-essentials-for-docs"></a><span data-ttu-id="d9797-103">Основные сведения о Git и GitHub для создания документации</span><span class="sxs-lookup"><span data-stu-id="d9797-103">Git and GitHub essentials for Docs</span></span>

## <a name="overview"></a><span data-ttu-id="d9797-104">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="d9797-104">Overview</span></span>

<span data-ttu-id="d9797-105">Как участник проекта по созданию документации вы будете использовать ряд инструментов и процессов.</span><span class="sxs-lookup"><span data-stu-id="d9797-105">As a contributor to Docs content, you will interact with multiple tools and processes.</span></span> <span data-ttu-id="d9797-106">Вы будете работать параллельно с другими участниками над одним и тем же проектом, иногда над тем же содержимым и в то же время.</span><span class="sxs-lookup"><span data-stu-id="d9797-106">You'll work in parallel with other contributors on the same project, potentially the exact same content, even at the same time.</span></span> <span data-ttu-id="d9797-107">Все это возможно благодаря программному обеспечению Git и GitHub.</span><span class="sxs-lookup"><span data-stu-id="d9797-107">This is all enabled through Git and GitHub software.</span></span>

<span data-ttu-id="d9797-108">Git — это система управления версиями с открытым исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="d9797-108">Git is an open-source version control system.</span></span> <span data-ttu-id="d9797-109">Она упрощает совместную работу над проектами такого типа с помощью *распределенной системы управления версиями* файлов, которые хранятся в *репозиториях*.</span><span class="sxs-lookup"><span data-stu-id="d9797-109">It facilitates this type of project collaboration through *distributed version control* of files that live in *repositories*.</span></span> <span data-ttu-id="d9797-110">По сути, Git позволяет интегрировать в определенный репозиторий потоки работы, выполненные несколькими участниками в течение определенного времени.</span><span class="sxs-lookup"><span data-stu-id="d9797-110">In essence, Git makes it possible to integrate streams of work done by multiple contributors over time, for a given repository.</span></span>

<span data-ttu-id="d9797-111">GitHub — это служба размещения в Интернете репозиториев Git, которые используются для хранения содержимого [docs.microsoft.com](https://docs.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="d9797-111">GitHub is a web-based hosting service for Git repositories, such as those used to store [docs.microsoft.com](https://docs.microsoft.com) content.</span></span> <span data-ttu-id="d9797-112">В GitHub размещается основной репозиторий всех проектов. Из этого репозитория участники копируют свою работу.</span><span class="sxs-lookup"><span data-stu-id="d9797-112">For any project, GitHub hosts the main repository, from which contributors can make copies for their own work.</span></span>

## <a name="git"></a><span data-ttu-id="d9797-113">Git</span><span class="sxs-lookup"><span data-stu-id="d9797-113">Git</span></span>

<span data-ttu-id="d9797-114">Если вы знакомы с централизованными системами управления версиями (например, Team Foundation Server, SharePoint или Visual SourceSafe), вы заметите, что Git использует уникальный рабочий процесс и специальную терминологию для поддержки распределенной модели.</span><span class="sxs-lookup"><span data-stu-id="d9797-114">If you're familiar with centralized version control systems (such as Team Foundation Server, SharePoint, or Visual SourceSafe), you will notice that Git has a unique contribution workflow and terminology to support its distributed model.</span></span> <span data-ttu-id="d9797-115">Например, в Git не блокируются файлы, как это обычно бывает, когда файл берут на редактирование или возвращают после редактирования.</span><span class="sxs-lookup"><span data-stu-id="d9797-115">For instance, there is no file locking that is normally associated with check-out/check-in operations.</span></span> <span data-ttu-id="d9797-116">На самом деле Git учитывает изменения на более тонком уровне, сравнивая файлы байт за байтом.</span><span class="sxs-lookup"><span data-stu-id="d9797-116">As a matter of fact, Git is concerned about changes at an even finer level, comparing files byte by byte.</span></span>

<span data-ttu-id="d9797-117">Git также использует многоуровневую структуру для хранения содержимого проекта и управления им.</span><span class="sxs-lookup"><span data-stu-id="d9797-117">Git also uses a tiered structure to store and manage content for a project:</span></span>

- <span data-ttu-id="d9797-118">*Репозиторий* — это *единица хранения* самого высокого уровня.</span><span class="sxs-lookup"><span data-stu-id="d9797-118">*Repository*: Also known as a *repo*, this is the highest unit of storage.</span></span> <span data-ttu-id="d9797-119">Репозиторий содержит одну или несколько ветвей.</span><span class="sxs-lookup"><span data-stu-id="d9797-119">A repository contains one or more branches.</span></span>
- <span data-ttu-id="d9797-120">*Ветвь* представляет собой единицу хранения, содержащую текущие файлы и папки, которые формируют содержимое проекта.</span><span class="sxs-lookup"><span data-stu-id="d9797-120">*Branch*: A unit of storage that contains the files and  folders that make up a project's content set.</span></span> <span data-ttu-id="d9797-121">Ветви используются для разделения потоков работы (обычно они называются версиями).</span><span class="sxs-lookup"><span data-stu-id="d9797-121">Branches separate streams of work (typically referred to as versions).</span></span> <span data-ttu-id="d9797-122">Участники всегда вносят изменения в содержимое в определенной ветви, и эти изменения привязаны к соответствующей ветви.</span><span class="sxs-lookup"><span data-stu-id="d9797-122">Contributions are always made and scoped to a specific branch.</span></span> <span data-ttu-id="d9797-123">Все репозитории содержат ветвь по умолчанию (обычно она называется главной) и одну или несколько ветвей, предназначенных для объединения с главной ветвью.</span><span class="sxs-lookup"><span data-stu-id="d9797-123">All repositories contain a default branch (typically named "master") and one or more branches that are destined to be merged back into the master branch.</span></span> <span data-ttu-id="d9797-124">Главная ветвь является текущей версией и единственным источником достоверных сведений для определенного проекта.</span><span class="sxs-lookup"><span data-stu-id="d9797-124">The master branch serves as the current version and "single source of truth" for the project.</span></span> <span data-ttu-id="d9797-125">Из этой родительской ветви создаются все остальные ветви в репозитории.</span><span class="sxs-lookup"><span data-stu-id="d9797-125">It's the parent from which all other branches in the repository are created.</span></span>

<span data-ttu-id="d9797-126">Участники взаимодействуют с Git, чтобы обновлять репозитории и управлять ими локально и на уровне GitHub.</span><span class="sxs-lookup"><span data-stu-id="d9797-126">Contributors interact with Git to update and manipulate repositories at both the local and GitHub levels:</span></span>

- <span data-ttu-id="d9797-127">Для локального взаимодействия участники используют такие инструменты, как консоль Git Bash, которая поддерживает команды Git для управления локальными репозиториями и обмена данными с репозиториями GitHub.</span><span class="sxs-lookup"><span data-stu-id="d9797-127">Locally through tools such as the Git Bash console, which supports Git commands for managing local repositories and communicating with GitHub repositories</span></span>
- <span data-ttu-id="d9797-128">Кроме того, участники используют сайт [www.github.com](https://www.github.com) с интегрированной системой Git для управления согласованием изменений, возвращаемых обратно в основной репозиторий.</span><span class="sxs-lookup"><span data-stu-id="d9797-128">Via [www.github.com](https://www.github.com), which integrates Git to manage the reconciliation of contributions that flow back into the main repository</span></span>

## <a name="github"></a><span data-ttu-id="d9797-129">GitHub</span><span class="sxs-lookup"><span data-stu-id="d9797-129">GitHub</span></span>

> [!NOTE]
> <span data-ttu-id="d9797-130">Хотя управление проекта Docs основано на использовании GitHub, некоторые команды используют Visual Studio Team Services для размещения репозиториев Git.</span><span class="sxs-lookup"><span data-stu-id="d9797-130">Although Docs guidance is based on using GitHub, some teams use Visual Studio Team Services to host Git repositories.</span></span> <span data-ttu-id="d9797-131">Клиент Visual Studio Team Explorer — это графический интерфейс для взаимодействия с репозиториями Team Services. Этот интерфейс является альтернативой использованию команд Git в командной строке.</span><span class="sxs-lookup"><span data-stu-id="d9797-131">The Visual Studio Team Explorer client provides a GUI for interacting with Team Services repositories, as an alternative to using Git commands through a command line.</span></span>
> </br>
> <span data-ttu-id="d9797-132">Кроме того, многие приведенные руководства разработаны в качестве рекомендаций, которые появились в результате многолетнего размещения содержимого службы Azure в GitHub.</span><span class="sxs-lookup"><span data-stu-id="d9797-132">Also, many of the following guidelines were developed as best practices from years of experience in hosting Azure service content in GitHub.</span></span> <span data-ttu-id="d9797-133">Они могут понадобиться для работы с некоторыми репозиториями Docs.</span><span class="sxs-lookup"><span data-stu-id="d9797-133">They might be required in some Docs repositories.</span></span>

<span data-ttu-id="d9797-134">Все рабочие процессы начинаются и заканчиваются на уровне GitHub, где хранится основной репозиторий любого проекта Docs.</span><span class="sxs-lookup"><span data-stu-id="d9797-134">All workflows begin and end at the GitHub level, where the main repository for any Docs project is stored.</span></span> <span data-ttu-id="d9797-135">Копии, создаваемые участниками для собственного использования, распространяются на нескольких компьютерах.</span><span class="sxs-lookup"><span data-stu-id="d9797-135">The copies that contributors create for their own use are distributed across multiple computers.</span></span> <span data-ttu-id="d9797-136">В итоге они согласовываются в основном репозитории GitHub проекта.</span><span class="sxs-lookup"><span data-stu-id="d9797-136">These copies are eventually reconciled back into the project's main GitHub repository.</span></span>

### <a name="directory-organization"></a><span data-ttu-id="d9797-137">Организация каталогов</span><span class="sxs-lookup"><span data-stu-id="d9797-137">Directory organization</span></span>

<span data-ttu-id="d9797-138">Как упоминалось ранее, стандартная или главная ветвь проекта является текущей версией содержимого проекта.</span><span class="sxs-lookup"><span data-stu-id="d9797-138">As mentioned earlier, a project's default/master branch serves as the current version of content for the project.</span></span> <span data-ttu-id="d9797-139">Содержимое главной ветви (и ветвей, созданных из нее) приблизительно согласовано с организацией статей на соответствующих страницах проекта Docs.</span><span class="sxs-lookup"><span data-stu-id="d9797-139">The content in the master branch--and branches created from it--is loosely aligned with the organization of the articles on the corresponding Docs pages.</span></span> <span data-ttu-id="d9797-140">Подкаталоги используются для разделения содержимого (например, служб), мультимедийного содержимого (например, файлов изображений) и файлов include, которые позволяют повторно использовать содержимое.</span><span class="sxs-lookup"><span data-stu-id="d9797-140">Subdirectories are used for separation of like content (such as services), media content (such as image files), and "include" files (which enable reuse of content).</span></span>

<span data-ttu-id="d9797-141">Основной каталог `articles` обычно находится в корне репозитория.</span><span class="sxs-lookup"><span data-stu-id="d9797-141">You can typically find a main `articles` directory off the root of the repository.</span></span> <span data-ttu-id="d9797-142">Этот каталог статей содержит набор подкаталогов.</span><span class="sxs-lookup"><span data-stu-id="d9797-142">The articles directory contains a set of subdirectories.</span></span> <span data-ttu-id="d9797-143">Статьи в подкаталогах имеют формат файлов Markdown с расширением *.md*.</span><span class="sxs-lookup"><span data-stu-id="d9797-143">Articles in the subdirectories are formatted as Markdown files that use an *.md* extension.</span></span> <span data-ttu-id="d9797-144">Некоторые репозитории, которые поддерживают несколько служб, например репозиторий [https://github.com/microsoft/Azure-Docs](https://github.com/microsoft/Azure-Docs), используют универсальный подкаталог `/articles`.</span><span class="sxs-lookup"><span data-stu-id="d9797-144">Some repositories that support multiple services use a generic `/articles` subdirectory, such as the [https://github.com/microsoft/Azure-Docs](https://github.com/microsoft/Azure-Docs) repository.</span></span> <span data-ttu-id="d9797-145">Другие репозитории, например [https://github.com/microsoft/IntuneDocs](https://github.com/microsoft/IntuneDocs), используют подкаталог, который называется как служба: `/IntuneDocs`.</span><span class="sxs-lookup"><span data-stu-id="d9797-145">Others might use a service-specific name, such as the [https://github.com/microsoft/IntuneDocs](https://github.com/microsoft/IntuneDocs) repository, which uses `/IntuneDocs`.</span></span>

<span data-ttu-id="d9797-146">В корне этого каталога находятся общие статьи, которые описывают службу или продукт в целом.</span><span class="sxs-lookup"><span data-stu-id="d9797-146">Within the root of this directory, you can find general articles that relate to the overall service or product.</span></span> <span data-ttu-id="d9797-147">Как правило, каталог содержит еще одну серию подкаталогов, которые соответствуют функциям и службам или распространенным сценариям.</span><span class="sxs-lookup"><span data-stu-id="d9797-147">And typically, you can then find another series of subdirectories that match the features/services or common scenarios.</span></span> <span data-ttu-id="d9797-148">Например, статьи, которые описывают службу виртуальных машин Azure, находятся в подкаталоге `/virtual-machines`, статьи "Изучение вопроса" службы Intune размещены в подкаталоге `/understand-explore`.</span><span class="sxs-lookup"><span data-stu-id="d9797-148">For instance, Azure "virtual machine" articles are in the `/virtual-machines` subdirectory, and Intune "understand and explore" articles are in the `/understand-explore` subdirectory.</span></span>

### <a name="media-subdirectory"></a><span data-ttu-id="d9797-149">Подкаталог Media</span><span class="sxs-lookup"><span data-stu-id="d9797-149">Media subdirectory</span></span>

<span data-ttu-id="d9797-150">В каждом каталоге находится подкаталог `/media` для соответствующих файлов мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="d9797-150">Each article directory contains a `/media` subdirectory for corresponding media files.</span></span> <span data-ttu-id="d9797-151">Файлы мультимедиа содержат изображения, используемые в статьях со ссылками на изображения.</span><span class="sxs-lookup"><span data-stu-id="d9797-151">Media files contain images used by articles that have image references.</span></span>

### <a name="includes-subdirectory"></a><span data-ttu-id="d9797-152">Подкаталог includes</span><span class="sxs-lookup"><span data-stu-id="d9797-152">Includes subdirectory</span></span>

<span data-ttu-id="d9797-153">Содержимое для многократного использования, которое является общим для двух или нескольких статей, помещается в подкаталог `/includes` основного каталога `articles`.</span><span class="sxs-lookup"><span data-stu-id="d9797-153">Whenever we have reusable content that is shared across two or more articles, it is placed in an `/includes` subdirectory off the main `articles` directory.</span></span> <span data-ttu-id="d9797-154">В файле Markdown, где используется включаемый файл, соответствующее расширение Markdown include помещается в расположение, на которое должна указывать ссылка на включаемый файл.</span><span class="sxs-lookup"><span data-stu-id="d9797-154">In a Markdown file that uses the include file, a corresponding "include" Markdown extension is placed in the location where the include file needs to be referenced.</span></span>

<span data-ttu-id="d9797-155">Дополнительные сведения см. в разделе о [включаемых файлах](how-to-write-use-markdown.md#includes) руководства "Использование разметки Markdown".</span><span class="sxs-lookup"><span data-stu-id="d9797-155">See [How to use Markdown: Includes](how-to-write-use-markdown.md#includes) for additional guidance.</span></span>

### <a name="markdown-file-template"></a><span data-ttu-id="d9797-156">Шаблон файла Markdown</span><span class="sxs-lookup"><span data-stu-id="d9797-156">Markdown file template</span></span>

<span data-ttu-id="d9797-157">Для удобства в корневом каталоге каждого репозитория обычно находится файл шаблона Markdown с именем `template.md`.</span><span class="sxs-lookup"><span data-stu-id="d9797-157">For convenience, the root directory of each repository typically contains a Markdown template file named `template.md`.</span></span> <span data-ttu-id="d9797-158">Его можно использовать как начальный файл для создания статьи с последующей отправкой в репозиторий.</span><span class="sxs-lookup"><span data-stu-id="d9797-158">You can use this template file as a "starter file" if you need to create a new article for submission to the repository.</span></span> <span data-ttu-id="d9797-159">Файл содержит следующие компоненты.</span><span class="sxs-lookup"><span data-stu-id="d9797-159">The file contains:</span></span>

- <span data-ttu-id="d9797-160">**Заголовок метаданных** в верхней части файла, разделенный двумя строками с тремя дефисами.</span><span class="sxs-lookup"><span data-stu-id="d9797-160">A **metadata header** at the top of the file, delineated by two, 3-hyphen lines.</span></span> <span data-ttu-id="d9797-161">Он содержит различные теги, используемые для отслеживания информации, относящейся к статье.</span><span class="sxs-lookup"><span data-stu-id="d9797-161">It contains the various tags used for tracking information related to the article.</span></span> <span data-ttu-id="d9797-162">Метаданные статьи обеспечивают дополнительные возможности. Например, можно указать ссылки на автора и участника, настроить строку навигации, добавить описание статьи.</span><span class="sxs-lookup"><span data-stu-id="d9797-162">Article metadata enables certain functionality, such as author attribution, contributor attribution, breadcrumbs, and article descriptions.</span></span> <span data-ttu-id="d9797-163">Они также обеспечивают оптимизации поисковых систем и позволяют Майкрософт оценивать качество содержимого.</span><span class="sxs-lookup"><span data-stu-id="d9797-163">It also includes SEO optimizations and reporting processes that Microsoft uses to evaluate the performance of the content.</span></span> <span data-ttu-id="d9797-164">Как видите, метаданные имеют большое значение.</span><span class="sxs-lookup"><span data-stu-id="d9797-164">So the metadata is important!</span></span>
- <span data-ttu-id="d9797-165">**Раздел метаданных** с описанием различных тегов и значений метаданных.</span><span class="sxs-lookup"><span data-stu-id="d9797-165">A **metadata section** that describes the various metadata tags and values.</span></span> <span data-ttu-id="d9797-166">Если вы не знаете, какие значения нужно использовать для раздела метаданных, их можно оставить пустыми или закомментировать с помощью начального хэштега (#). Так рецензент запроса на вытягивание в репозитории сможет проверить или заполнить их.</span><span class="sxs-lookup"><span data-stu-id="d9797-166">If you're unsure of the values to use for the metadata section, you can leave them blank or comment them with a leading hashtag (#), and they will be reviewed/completed by the pull request reviewer for the repository.</span></span>
- <span data-ttu-id="d9797-167">Различные **примеры использования разметки Markdown** для форматирования элементов статьи.</span><span class="sxs-lookup"><span data-stu-id="d9797-167">Various **examples of using Markdown** to format the elements of an article.</span></span>
- <span data-ttu-id="d9797-168">Общие **инструкции по использованию расширений разметки Markdown**, которые можно применять для различных типов оповещений.</span><span class="sxs-lookup"><span data-stu-id="d9797-168">General **instructions on the use of Markdown extensions**, which you can use for various types of alerts.</span></span>
- <span data-ttu-id="d9797-169">Примеры **встраивания видео** с помощью iframe.</span><span class="sxs-lookup"><span data-stu-id="d9797-169">Examples of **embedding video** by using an iframe.</span></span>
- <span data-ttu-id="d9797-170">Общие **инструкции по использованию расширений docs.microsoft.com**, которые можно применять для специальных элементов управления, таких как кнопки и селекторы.</span><span class="sxs-lookup"><span data-stu-id="d9797-170">General **instructions on the use of docs.microsoft.com extensions**, which you can use for special controls such as buttons and selectors.</span></span>

## <a name="pull-requests"></a><span data-ttu-id="d9797-171">Запросы на вытягивание</span><span class="sxs-lookup"><span data-stu-id="d9797-171">Pull requests</span></span>

<span data-ttu-id="d9797-172">*Запрос на вытягивание* — используя этот удобный способ, участник предлагает набор изменений для внесения в стандартную ветвь.</span><span class="sxs-lookup"><span data-stu-id="d9797-172">A *pull request* provides a convenient way for a contributor to propose a set of changes that will be applied to the default branch.</span></span> <span data-ttu-id="d9797-173">Изменения (они также называются *фиксациями*) хранятся в ветви участника. GitHub использует их для моделирования результатов их *объединения* со стандартной ветвью.</span><span class="sxs-lookup"><span data-stu-id="d9797-173">The changes (also known as *commits*) are stored in a contributor's branch, so GitHub can first model the impact of *merging* them into the default branch.</span></span> <span data-ttu-id="d9797-174">Запрос на вытягивание также служит механизмом для предоставления участнику отзыва рецензента запроса. Рецензент отправляет участнику отзыв после процесса сборки и проверки, чтобы решить потенциальные проблемы или вопросы до того, как изменения будут объединены в стандартной ветви.</span><span class="sxs-lookup"><span data-stu-id="d9797-174">A pull request also serves as a mechanism to provide the contributor with feedback from a build/validation process, the pull request reviewer, to resolve potential issues or questions before the changes are merged into the default branch.</span></span>

<span data-ttu-id="d9797-175">В зависимости от размера предлагаемых изменений можно воспользоваться двумя способами размещения материалов с помощью запроса на вытягивание.</span><span class="sxs-lookup"><span data-stu-id="d9797-175">There are two ways to contribute by pull request, depending on the size of changes that you want to propose.</span></span> <span data-ttu-id="d9797-176">Дополнительные сведения см. в статье [Рабочий процесс для участников GitHub: незначительные или эпизодические изменения](how-to-write-workflows-major.md).</span><span class="sxs-lookup"><span data-stu-id="d9797-176">We will cover this in detail later, in the [GitHub workflow](how-to-write-workflows-major.md) section of this guide.</span></span>

<!---- Reference links for Docs landing pages, associated GitHub repositories, and related Forums matrix. ------------------>
<!---- PLEASE INSERT URLS IN ASCENDING SORT ORDER, AND REMOVE LOCALE SEGMENT FROM URLS (that is, en-us) FOR LOCALIZED FORUMS! -->
<!---- NOTE: these links are saved for future use in another/new article; no longer used above in this article --->
[Visual-Studio-Page]:(https://docs.microsoft.com/en-us/visualstudio/index)
[Visual-Studio-Repo-Internal]:(https://github.com/Microsoft/vsdocs)
[Visual-Studio-Repo-External]:(https://github.com/Microsoft/visualstudio-docs)
[Visual-Studio-SO]: (https://stackoverflow.com/search?q=Visual+Studio+2017)
[Dotnet-Page]: https://docs.microsoft.com/dotnet
[Dotnet-Core-Page]: https://docs.microsoft.com/dotnet/articles/welcome
[Dotnet-Core-Repo]: https://github.com/dotnet/docs
[EM-ATA-Land]: https://docs.microsoft.com/advanced-threat-analytics/
[EM-ATA-Repo]: https://github.com/Microsoft/ATADocs
[EM-AzureAD-Land]: https://docs.microsoft.com/active-directory/
[EM-AzureAD-Repo]: https://github.com/Azure/azure-content/tree/master/articles/active-directory/
[EM-AzureRMS-Land]: https://docs.microsoft.com/rights-management/
[EM-AzureRMS-Repo]: https://github.com/Microsoft/Azure-RMSDocs
[EM-Intune-Land]: https://docs.microsoft.com/intune/
[EM-Intune-Repo]: https://github.com/microsoft/intuneDocs
[EM-Land-Page]: https://docs.microsoft.com/enterprise-mobility/
[EM-Land-Repo]: https://github.com/Microsoft/EMDocs/
[EM-MFA-Land]: https://docs.microsoft.com/multi-factor-authentication/
[EM-MFA-Repo]: https://github.com/Azure/azure-content/tree/master/articles/multi-factor-authentication
[EM-MIM-Land]: https://docs.microsoft.com/microsoft-identity-manager/
[EM-MIM-Repo]: https://github.com/Microsoft/MIMDocs
[EM-RemoteApp-Land]: https://docs.microsoft.com/en-us/remoteapp/
[EM-RemoteApp-Repo]: https://github.com/Azure/azure-content/tree/master/articles/remoteapp
[Forum-MSDN-ATA]: https://social.technet.microsoft.com/Forums/en-US/home?forum=mata
[Forum-MSDN-AzureAD]: https://social.msdn.microsoft.com/Forums/en-US/home?forum=WindowsAzureAD
[Forum-MSDN-AzureRMS]: https://social.technet.microsoft.com/Forums/en-US/home?forum=rmsapps%2Crmscloud&filter=alltypes&sort=lastpostdesc
[Forum-MSDN-EM]: https://social.technet.microsoft.com/Forums/en-US/home?sort=relevancedesc&brandIgnore=True&searchTerm=Enterprise+Mobility
[Forum-MSDN-Intune]: https://social.technet.microsoft.com/Forums/en-us/home?category=microsoftintune
[Forum-MSDN-Main]: https://social.msdn.microsoft.com/Forums/home
[Forum-MSDN-MFA]: https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowsazureactiveauthentication
[Forum-MSDN-MIM]: https://social.technet.microsoft.com/Forums/en-US/home?category=identitymanagement
[Forum-MSDN-RemoteApp]: https://social.technet.microsoft.com/Forums/en-US/home?filter=alltypes&brandIgnore=True&sort=relevancedesc&searchTerm=Azure+Remote+or+RemoteApp
[Forum-SO-AzureAD]: https://stackoverflow.com/questions/tagged/azure-active-directory
[Forum-SO-AzureRMS]: https://stackoverflow.com/questions/tagged/rights-management
[Forum-SO-Dotnet]: https://stackoverflow.com/questions/tagged/.net
[Forum-SO-Dotnet-Core]: https://stackoverflow.com/questions/tagged/.net-core
[Forum-SO-Main]: https://stackoverflow.com/tags
[Forum-SO-Intune]: https://stackoverflow.com/questions/tagged/intune
[Forum-SO-MFA]: https://stackoverflow.com/search?q=%5Bazure%5D+multi-factor
[Forum-SO-MIM]: https://stackoverflow.com/search?q=Microsoft+Identity+Manager
[Forum-SO-RemoteApp]: https://stackoverflow.com/questions/tagged/remoteapp
[Forum-TechNet-Main]: https://social.technet.microsoft.com/Forums/home
[Forum-Yammer-AzureRMS]: https://www.yammer.com/AskIPTeam
[Forum-Yammer-Main]: https://www.yammer.com/
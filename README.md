USE [master]
GO
/****** Object:  Database [MemoryMatch]    Script Date: 1/29/2019 1:22:29 PM ******/
CREATE DATABASE [MemoryMatch]
 CONTAINMENT = NONE
 ON  PRIMARY 
( NAME = N'MemoryMatch', FILENAME = N'D:\Program Files\MSSQL14.SQLEXPRESS\MSSQL\DATA\MemoryMatch.mdf' , SIZE = 8192KB , MAXSIZE = UNLIMITED, FILEGROWTH = 65536KB )
 LOG ON 
( NAME = N'MemoryMatch_log', FILENAME = N'D:\Program Files\MSSQL14.SQLEXPRESS\MSSQL\DATA\MemoryMatch_log.ldf' , SIZE = 8192KB , MAXSIZE = 2048GB , FILEGROWTH = 65536KB )
GO
ALTER DATABASE [MemoryMatch] SET COMPATIBILITY_LEVEL = 140
GO
IF (1 = FULLTEXTSERVICEPROPERTY('IsFullTextInstalled'))
begin
EXEC [MemoryMatch].[dbo].[sp_fulltext_database] @action = 'enable'
end
GO
ALTER DATABASE [MemoryMatch] SET ANSI_NULL_DEFAULT OFF 
GO
ALTER DATABASE [MemoryMatch] SET ANSI_NULLS OFF 
GO
ALTER DATABASE [MemoryMatch] SET ANSI_PADDING OFF 
GO
ALTER DATABASE [MemoryMatch] SET ANSI_WARNINGS OFF 
GO
ALTER DATABASE [MemoryMatch] SET ARITHABORT OFF 
GO
ALTER DATABASE [MemoryMatch] SET AUTO_CLOSE OFF 
GO
ALTER DATABASE [MemoryMatch] SET AUTO_SHRINK OFF 
GO
ALTER DATABASE [MemoryMatch] SET AUTO_UPDATE_STATISTICS ON 
GO
ALTER DATABASE [MemoryMatch] SET CURSOR_CLOSE_ON_COMMIT OFF 
GO
ALTER DATABASE [MemoryMatch] SET CURSOR_DEFAULT  GLOBAL 
GO
ALTER DATABASE [MemoryMatch] SET CONCAT_NULL_YIELDS_NULL OFF 
GO
ALTER DATABASE [MemoryMatch] SET NUMERIC_ROUNDABORT OFF 
GO
ALTER DATABASE [MemoryMatch] SET QUOTED_IDENTIFIER OFF 
GO
ALTER DATABASE [MemoryMatch] SET RECURSIVE_TRIGGERS OFF 
GO
ALTER DATABASE [MemoryMatch] SET  DISABLE_BROKER 
GO
ALTER DATABASE [MemoryMatch] SET AUTO_UPDATE_STATISTICS_ASYNC OFF 
GO
ALTER DATABASE [MemoryMatch] SET DATE_CORRELATION_OPTIMIZATION OFF 
GO
ALTER DATABASE [MemoryMatch] SET TRUSTWORTHY OFF 
GO
ALTER DATABASE [MemoryMatch] SET ALLOW_SNAPSHOT_ISOLATION OFF 
GO
ALTER DATABASE [MemoryMatch] SET PARAMETERIZATION SIMPLE 
GO
ALTER DATABASE [MemoryMatch] SET READ_COMMITTED_SNAPSHOT OFF 
GO
ALTER DATABASE [MemoryMatch] SET HONOR_BROKER_PRIORITY OFF 
GO
ALTER DATABASE [MemoryMatch] SET RECOVERY SIMPLE 
GO
ALTER DATABASE [MemoryMatch] SET  MULTI_USER 
GO
ALTER DATABASE [MemoryMatch] SET PAGE_VERIFY CHECKSUM  
GO
ALTER DATABASE [MemoryMatch] SET DB_CHAINING OFF 
GO
ALTER DATABASE [MemoryMatch] SET FILESTREAM( NON_TRANSACTED_ACCESS = OFF ) 
GO
ALTER DATABASE [MemoryMatch] SET TARGET_RECOVERY_TIME = 60 SECONDS 
GO
ALTER DATABASE [MemoryMatch] SET DELAYED_DURABILITY = DISABLED 
GO
ALTER DATABASE [MemoryMatch] SET QUERY_STORE = OFF
GO
USE [MemoryMatch]
GO
ALTER DATABASE SCOPED CONFIGURATION SET IDENTITY_CACHE = ON;
GO
ALTER DATABASE SCOPED CONFIGURATION SET LEGACY_CARDINALITY_ESTIMATION = OFF;
GO
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION = PRIMARY;
GO
ALTER DATABASE SCOPED CONFIGURATION SET MAXDOP = 0;
GO
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP = PRIMARY;
GO
ALTER DATABASE SCOPED CONFIGURATION SET PARAMETER_SNIFFING = ON;
GO
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING = PRIMARY;
GO
ALTER DATABASE SCOPED CONFIGURATION SET QUERY_OPTIMIZER_HOTFIXES = OFF;
GO
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET QUERY_OPTIMIZER_HOTFIXES = PRIMARY;
GO
USE [MemoryMatch]
GO
/****** Object:  Table [dbo].[ContactUsMessages]    Script Date: 1/29/2019 1:22:29 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ContactUsMessages](
	[MessageID] [int] IDENTITY(1,1) NOT NULL,
	[MessageDateAdded] [datetime] NULL,
	[Phone] [nvarchar](50) NULL,
	[Email] [nvarchar](50) NULL,
	[MessageContent] [nvarchar](max) NULL,
 CONSTRAINT [PK_ContactUsMessages] PRIMARY KEY CLUSTERED 
(
	[MessageID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Feedbacks]    Script Date: 1/29/2019 1:22:30 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Feedbacks](
	[FeedbackID] [int] IDENTITY(1,1) NOT NULL,
	[UserID] [int] NULL,
	[FeedbackDateAdded] [datetime] NULL,
	[FeedbackText] [nvarchar](max) NULL,
 CONSTRAINT [PK_UsersFeedback] PRIMARY KEY CLUSTERED 
(
	[FeedbackID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[GameResults]    Script Date: 1/29/2019 1:22:30 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[GameResults](
	[GameResultID] [int] IDENTITY(1,1) NOT NULL,
	[UserID] [int] NULL,
	[DateAdded] [datetime] NULL,
	[TimeSpan] [time](7) NULL,
	[StepsNumber] [int] NULL,
 CONSTRAINT [PK_GameResults] PRIMARY KEY CLUSTERED 
(
	[GameResultID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Images]    Script Date: 1/29/2019 1:22:30 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Images](
	[ImageID] [int] IDENTITY(1,1) NOT NULL,
	[ImageName] [nvarchar](50) NULL,
	[ImageType] [nvarchar](10) NULL,
 CONSTRAINT [PK_Images] PRIMARY KEY CLUSTERED 
(
	[ImageID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Users]    Script Date: 1/29/2019 1:22:30 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Users](
	[UserID] [int] IDENTITY(1,1) NOT NULL,
	[FullName] [nvarchar](50) NULL,
	[Username] [nvarchar](20) NULL,
	[Password] [nvarchar](20) NULL,
	[Email] [nvarchar](30) NULL,
	[BirthDate] [date] NULL,
 CONSTRAINT [PK_UsersDetails] PRIMARY KEY CLUSTERED 
(
	[UserID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
SET IDENTITY_INSERT [dbo].[ContactUsMessages] ON 

INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (1, NULL, N'055-1232321', N'bla@gmail.com', N'What do you want from me, it''s not how it use to be')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (2, NULL, N'055-1232321', N'bla@gmail.com', N'What do you want from me, it''s not how it use to be')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (3, NULL, N'055-1232321', N'bla@gmail.com', N'What do you want from me, it''s not how it use to be')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (4, CAST(N'2018-11-21T15:00:06.357' AS DateTime), N'055-1232321', N'bla@gmail.com', N'What do you want from me, it''s not how it use to be')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (5, CAST(N'2018-11-21T15:29:21.920' AS DateTime), N'055-1232321', N'bla@gmail.com', N'What do you want from me, it''s not how it use to be')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (8, CAST(N'2018-11-21T15:31:11.163' AS DateTime), N'055-1232321', N'bla@gmail.com', N'bla')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (1002, CAST(N'2018-12-06T16:41:27.840' AS DateTime), N'054-2121345', N'bla@gmail.com', N'I''ll let it all just rain on me')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (2002, CAST(N'2018-12-13T10:58:48.657' AS DateTime), N'050-1232123', N'ron@gmail.com', N'Sup Everybody?')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (2003, CAST(N'2018-12-21T12:08:33.937' AS DateTime), N'0527687687', N'blalala@gmail.com', N'ohoih')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (2004, CAST(N'2019-01-13T15:58:42.793' AS DateTime), N'0538768755', N'dfhd@gmail.com', N'What''s up')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (2005, CAST(N'2019-01-13T16:10:05.340' AS DateTime), N'', NULL, N'Hello Hello')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (2006, CAST(N'2019-01-13T16:11:31.103' AS DateTime), N'', NULL, N'hayushhh')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (2007, CAST(N'2019-01-13T16:12:29.387' AS DateTime), N'', NULL, N'dadlkjdc')
INSERT [dbo].[ContactUsMessages] ([MessageID], [MessageDateAdded], [Phone], [Email], [MessageContent]) VALUES (2008, CAST(N'2019-01-13T16:35:16.653' AS DateTime), NULL, NULL, N'hayush hayush')
SET IDENTITY_INSERT [dbo].[ContactUsMessages] OFF
SET IDENTITY_INSERT [dbo].[Feedbacks] ON 

INSERT [dbo].[Feedbacks] ([FeedbackID], [UserID], [FeedbackDateAdded], [FeedbackText]) VALUES (3, 10, CAST(N'2018-12-09T17:46:35.487' AS DateTime), N'some text ble bla bla')
INSERT [dbo].[Feedbacks] ([FeedbackID], [UserID], [FeedbackDateAdded], [FeedbackText]) VALUES (4, 13, CAST(N'2018-12-16T20:18:19.030' AS DateTime), N'osidhvsdovh')
INSERT [dbo].[Feedbacks] ([FeedbackID], [UserID], [FeedbackDateAdded], [FeedbackText]) VALUES (5, 13, CAST(N'2018-12-17T12:30:41.803' AS DateTime), N'feedback')
INSERT [dbo].[Feedbacks] ([FeedbackID], [UserID], [FeedbackDateAdded], [FeedbackText]) VALUES (6, 13, CAST(N'2018-12-17T12:34:25.083' AS DateTime), N'feedback')
INSERT [dbo].[Feedbacks] ([FeedbackID], [UserID], [FeedbackDateAdded], [FeedbackText]) VALUES (7, 13, CAST(N'2018-12-20T08:41:41.110' AS DateTime), N'Hello and  good morning')
INSERT [dbo].[Feedbacks] ([FeedbackID], [UserID], [FeedbackDateAdded], [FeedbackText]) VALUES (8, 13, CAST(N'2019-01-14T13:53:05.600' AS DateTime), N'lkljnlj')
INSERT [dbo].[Feedbacks] ([FeedbackID], [UserID], [FeedbackDateAdded], [FeedbackText]) VALUES (9, 13, CAST(N'2019-01-14T14:56:20.233' AS DateTime), N'Hello world!')
INSERT [dbo].[Feedbacks] ([FeedbackID], [UserID], [FeedbackDateAdded], [FeedbackText]) VALUES (1008, 1018, CAST(N'2019-01-28T18:55:09.327' AS DateTime), N'Nice Game!')
SET IDENTITY_INSERT [dbo].[Feedbacks] OFF
SET IDENTITY_INSERT [dbo].[GameResults] ON 

INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (1, 10, CAST(N'2018-12-09T17:07:21.583' AS DateTime), CAST(N'00:05:00' AS Time), 25)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (2, 13, CAST(N'2019-01-05T11:38:51.737' AS DateTime), CAST(N'00:01:02' AS Time), 38)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (3, 13, CAST(N'2019-01-05T11:45:56.623' AS DateTime), CAST(N'00:00:50' AS Time), 36)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (4, 13, CAST(N'2019-01-07T14:13:10.493' AS DateTime), CAST(N'00:01:07' AS Time), 48)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (5, 13, CAST(N'2019-01-07T14:39:05.593' AS DateTime), CAST(N'00:01:15' AS Time), 42)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (6, 13, CAST(N'2019-01-07T14:41:40.107' AS DateTime), CAST(N'00:01:00' AS Time), 36)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (7, 1018, CAST(N'2019-01-16T19:32:03.213' AS DateTime), CAST(N'00:03:25' AS Time), 46)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (8, 1018, CAST(N'2019-01-16T19:38:29.687' AS DateTime), CAST(N'00:03:12' AS Time), 64)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (9, 1018, CAST(N'2019-01-17T07:48:45.527' AS DateTime), CAST(N'00:00:59' AS Time), 34)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (10, 1018, CAST(N'2019-01-17T07:53:40.947' AS DateTime), CAST(N'00:01:00' AS Time), 40)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (1007, 1018, CAST(N'2019-01-27T20:33:57.480' AS DateTime), CAST(N'00:01:16' AS Time), 40)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (1008, 1018, CAST(N'2019-01-28T19:58:30.090' AS DateTime), CAST(N'00:00:57' AS Time), 34)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (1009, 1018, CAST(N'2019-01-28T20:07:51.810' AS DateTime), CAST(N'00:02:45' AS Time), 48)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (1010, 1018, CAST(N'2019-01-28T20:14:12.660' AS DateTime), CAST(N'00:01:27' AS Time), 56)
INSERT [dbo].[GameResults] ([GameResultID], [UserID], [DateAdded], [TimeSpan], [StepsNumber]) VALUES (1011, 1018, CAST(N'2019-01-28T20:17:18.427' AS DateTime), CAST(N'00:01:08' AS Time), 48)
SET IDENTITY_INSERT [dbo].[GameResults] OFF
SET IDENTITY_INSERT [dbo].[Images] ON 

INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (1, N'sloth1.jpg', N'frontCard')
INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (2, N'sloth2.jpg', N'frontCard')
INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (3, N'sloth3.jpg', N'frontCard')
INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (4, N'sloth4.jpg', N'frontCard')
INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (5, N'sloth5.jpg', N'frontCard')
INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (6, N'sloth6.jpg', N'frontCard')
INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (7, N'sloth7.jpg', N'frontCard')
INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (8, N'sloth8.jpg', N'frontCard')
INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (9, N'sloth9.jpg', N'frontCard')
INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (10, N'sloth10.jpg', N'frontCard')
INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (11, N'backImage.jpg', N'backCard')
INSERT [dbo].[Images] ([ImageID], [ImageName], [ImageType]) VALUES (12, N'backgroundSloth.jpg', N'background')
SET IDENTITY_INSERT [dbo].[Images] OFF
SET IDENTITY_INSERT [dbo].[Users] ON 

INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (1, N'Adi Algrabli', N'AdiA', N'123456', N'adialgrabli@gmail.com', CAST(N'1988-10-17' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (2, N'Adi Algrabli', N'AdiA', N'123456', N'adialgrabli@gmail.com', CAST(N'1988-10-17' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (3, N'Adi Algrabli', N'AdiA', N'123456', N'adialgrabli@gmail.com', CAST(N'1988-10-17' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (4, N'john doe', N'jd', N'password', N'bla@gmail.com', CAST(N'2018-11-21' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (5, NULL, N'Robby', N'123456', N'rob@gmail.com', CAST(N'1986-02-13' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (6, NULL, N'blablblabl', N'123456', N'bla@gmail.com', NULL)
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (7, NULL, N'Moishale', N'123456`', N'moish@gmail.com', CAST(N'2014-10-29' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (8, NULL, N'Moishale', N'123456`', N'moish@gmail.com', CAST(N'2014-10-29' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (9, N'Kippi Ben Kipod', N'Kippush', N'123444', N'kippi@gmail.com', CAST(N'1972-03-24' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (10, N'Ugi Fletzet', N'Ugush', N'121212', N'ugi@gmail.com', CAST(N'2000-08-25' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (11, N'abc def', N'bla_25', N'Abc123456', NULL, NULL)
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (12, N'abc def', N'bla_25', N'Abc11223456', N'blablinmb@gmail.com', CAST(N'2003-12-12' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (13, N'Chandler Bing', N'Chad', N'Ch123456', N'chandler@gmail.com', CAST(N'2016-02-01' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (14, N'Chandler Bing', N'Chaddi', N'Chad121212', N'chan@gmail.com', CAST(N'2012-01-01' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (1013, N'Ploni Almoni', N'Plonush', N'Pl123456', N'ploni@gmail.com', CAST(N'2016-02-02' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (1014, N'Daniello Ro', N'Dani', N'Da123456', N'Daniello@gmail.com', NULL)
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (1015, N'Mila Kunis', N'Mila', N'Mila123456', N'mila@gmail.com', CAST(N'2015-02-02' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (1016, N'Ashton Kutcher', N'Ashton', N'Ash123456', N'ashton@gmail.com', CAST(N'2014-10-29' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (1017, N'John Doe', N'Johnny', N'John1234', N'john@gmail.com', CAST(N'2018-07-09' AS Date))
INSERT [dbo].[Users] ([UserID], [FullName], [Username], [Password], [Email], [BirthDate]) VALUES (1018, N'Jinny yo', N'Jinny', N'Jinny12346', NULL, NULL)
SET IDENTITY_INSERT [dbo].[Users] OFF
ALTER TABLE [dbo].[ContactUsMessages] ADD  CONSTRAINT [DF_ContactUsMessages_MessageDateAdded]  DEFAULT (getdate()) FOR [MessageDateAdded]
GO
ALTER TABLE [dbo].[Feedbacks] ADD  CONSTRAINT [DF_UsersFeedback_FeedbackDateAdded]  DEFAULT (getdate()) FOR [FeedbackDateAdded]
GO
ALTER TABLE [dbo].[GameResults] ADD  CONSTRAINT [DF_GameResults_DateAdded]  DEFAULT (getdate()) FOR [DateAdded]
GO
ALTER TABLE [dbo].[Feedbacks]  WITH CHECK ADD  CONSTRAINT [FK_Feedbacks_Users] FOREIGN KEY([UserID])
REFERENCES [dbo].[Users] ([UserID])
GO
ALTER TABLE [dbo].[Feedbacks] CHECK CONSTRAINT [FK_Feedbacks_Users]
GO
ALTER TABLE [dbo].[GameResults]  WITH CHECK ADD  CONSTRAINT [FK_GameResults_Users] FOREIGN KEY([UserID])
REFERENCES [dbo].[Users] ([UserID])
GO
ALTER TABLE [dbo].[GameResults] CHECK CONSTRAINT [FK_GameResults_Users]
GO
USE [master]
GO
ALTER DATABASE [MemoryMatch] SET  READ_WRITE 
GO

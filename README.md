import React from 'react'
import { Avatar, AvatarFallback, AvatarImage } from "@/components/ui/avatar"
import { Button } from "@/components/ui/button"
import { Input } from "@/components/ui/input"
import { Textarea } from "@/components/ui/textarea"
import { ScrollArea } from "@/components/ui/scroll-area"
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs"
import { Bell, Home, Mail, Search, Send, User } from 'lucide-react'

export default function MeetMeApp() {
  return (
    <div className="flex h-screen bg-gray-100">
      {/* Sidebar */}
      <aside className="w-64 bg-primary text-primary-foreground p-4">
        <h1 className="text-2xl font-bold mb-8">MeetMe</h1>
        <nav className="space-y-4">
          <Button variant="ghost" className="w-full justify-start">
            <Home className="mr-2 h-4 w-4" />
            Home
          </Button>
          <Button variant="ghost" className="w-full justify-start">
            <Search className="mr-2 h-4 w-4" />
            Explore
          </Button>
          <Button variant="ghost" className="w-full justify-start">
            <Bell className="mr-2 h-4 w-4" />
            Notifications
          </Button>
          <Button variant="ghost" className="w-full justify-start">
            <Mail className="mr-2 h-4 w-4" />
            Messages
          </Button>
          <Button variant="ghost" className="w-full justify-start">
            <User className="mr-2 h-4 w-4" />
            Profile
          </Button>
        </nav>
      </aside>

      {/* Main content */}
      <main className="flex-1 flex">
        {/* Feed */}
        <section className="flex-1 border-r border-gray-200">
          <header className="bg-background/95 backdrop-blur supports-[backdrop-filter]:bg-background/60 sticky top-0 z-10 w-full border-b border-gray-200 p-4">
            <h2 className="text-lg font-semibold">Home</h2>
          </header>

          {/* Compose Meet */}
          <div className="p-4 border-b border-gray-200">
            <Textarea placeholder="What's happening?" className="mb-2" />
            <div className="flex justify-between items-center">
              <Button variant="outline" size="sm">Add Image</Button>
              <Button size="sm">Meet</Button>
            </div>
          </div>

          {/* Feed content */}
          <ScrollArea className="h-[calc(100vh-180px)]">
            {[1, 2, 3, 4, 5].map((i) => (
              <div key={i} className="p-4 border-b border-gray-200">
                <div className="flex space-x-3">
                  <Avatar>
                    <AvatarImage src={`/placeholder-user-${i}.jpg`} alt={`User ${i}`} />
                    <AvatarFallback>U{i}</AvatarFallback>
                  </Avatar>
                  <div className="flex-1">
                    <div className="flex items-center space-x-2">
                      <h3 className="font-semibold">User {i}</h3>
                      <span className="text-sm text-gray-500">@user{i}</span>
                      <span className="text-sm text-gray-500">· 1h</span>
                    </div>
                    <p className="mt-1">This is a sample meet (tweet) for the MeetMe app. It's great to connect with everyone here!</p>
                    <div className="mt-2 flex space-x-4">
                      <Button variant="ghost" size="sm">Like</Button>
                      <Button variant="ghost" size="sm">Remeet</Button>
                      <Button variant="ghost" size="sm">Reply</Button>
                    </div>
                  </div>
                </div>
              </div>
            ))}
          </ScrollArea>
        </section>

        {/* Messaging sidebar */}
        <aside className="w-80 bg-background border-l border-gray-200">
          <Tabs defaultValue="messages" className="w-full">
            <TabsList className="w-full">
              <TabsTrigger value="messages" className="flex-1">Messages</TabsTrigger>
              <TabsTrigger value="online" className="flex-1">Online</TabsTrigger>
            </TabsList>
            <TabsContent value="messages" className="p-4">
              <Input placeholder="Search messages" className="mb-4" />
              <ScrollArea className="h-[calc(100vh-200px)]">
                {[1, 2, 3, 4, 5].map((i) => (
                  <div key={i} className="flex items-center space-x-3 mb-4 cursor-pointer hover:bg-gray-100 p-2 rounded">
                    <Avatar>
                      <AvatarImage src={`/placeholder-user-${i}.jpg`} alt={`User ${i}`} />
                      <AvatarFallback>U{i}</AvatarFallback>
                    </Avatar>
                    <div>
                      <h4 className="font-semibold">User {i}</h4>
                      <p className="text-sm text-gray-500">Last message...</p>
                    </div>
                  </div>
                ))}
              </ScrollArea>
            </TabsContent>
            <TabsContent value="online" className="p-4">
              <ScrollArea className="h-[calc(100vh-160px)]">
                {[1, 2, 3].map((i) => (
                  <div key={i} className="flex items-center space-x-3 mb-4">
                    <Avatar>
                      <AvatarImage src={`/placeholder-user-${i}.jpg`} alt={`User ${i}`} />
                      <AvatarFallback>U{i}</AvatarFallback>
                    </Avatar>
                    <div>
                      <h4 className="font-semibold">User {i}</h4>
                      <p className="text-sm text-green-500">Online</p>
                    </div>
                  </div>
                ))}
              </ScrollArea>
            </TabsContent>
          </Tabs>
        </aside>
      </main>
    </div>
  )
}

# Building webservices in Go

There is an excellent talk by Mat Ryer about HTTP web services 
- https://www.youtube.com/watch?v=rWBSMsLG8po

- Create a `routes.go` file to handle all your routes.
   - ie
   ```
   func (s *server) routes() {
           s.router.Get("/api/", s.handleAPI())
           s.router.Get("/About", s.handleAbout())
           s.router.Get("/", s.handleIndex())
           ```

These handlers hang off the server.
   - 
   ```
   func (s *sever) handleSomething() http.HanlerFunc {
     }
   ```
     
- Create handler namings

  handleTasksCreate
  handleTaskDone

  handleAuthLogin
  handleAuthLogout


